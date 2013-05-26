begin
  require 'rubygems'
  require 'bundler'
rescue LoadError
  raise "Could not load the bundler gem. Install it with `gem install bundler`."
end

begin
  Bundler.setup
rescue Bundler::GemNotFound
  raise RuntimeError, "Bundler couldn't find some gems. Did you run `bundle install`?"
end

task :default => :server
 
desc 'Build and deploy'
task :deploy do
  sh 'rsync -crtzh --progress --delete _site/ penso@plouf.4push.com:/data/www/fabien/penso.info/htdocs/'
end

desc 'Notify Google of the new sitemap'
task :sitemap do
	require 'net/http'
	require 'uri'
	puts '* Pinging Google about our sitemap'
	Net::HTTP.get(
		'www.google.com',
		'/webmasters/tools/ping?sitemap=' +
		URI.escape('http://blog.penso.info/sitemap.xml')
	)
end

desc 'Ping pingomatic'
task :pingomatic do
  begin
    require 'xmlrpc/client'
    puts '* Pinging ping-o-matic'
    XMLRPC::Client.new('rpc.pingomatic.com', '/').call('weblogUpdates.extendedPing', 'Fabien Penso' , 'http://blog.penso.info', 'http://blog.penso.info/atom.xml')
  rescue LoadError
    puts '! Could not ping ping-o-matic, because XMLRPC::Client could not be found.'
  end
end

desc 'Removing Comments from previous import'
task :cleanposts do
	require 'htmlentities'
	coder = HTMLEntities.new

	YAML::ENGINE.yamler = "psych"
	keep_vars = %W(categories layout date title author description photo)
	Dir.glob("_posts/*.md").each do |file|
		puts "Working on #{file}"

		content = File.read(file)
		thing = YAML.load_file(file)
		headers = thing.select{|key, value|
			keep_vars.include?(key)
		}

		if (md = content.match(/^(?<metadata>---\s*\n.*?\n?)^(---\s*$\n?)/m))
			contents = md.post_match
			metadata = YAML.load(md[:metadata])

			File.open(file, 'wb') do |opened_file|
				opened_file.write YAML.dump(headers)
				opened_file.write "---\n"
				opened_file.write coder.decode(contents).gsub(/\r\n/, "\n")
			end
		end
	end
end
