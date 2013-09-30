namespace :fuseki do
	desc "Install jena-fuseki-1.0.0"
	task :install do
		if File.directory?("vendor/jena-fuseki-1.0.0") 
			puts "vendor/jena-fuseki-1.0.0/ already exists.  Nothing to do."
			next
		end

		puts "Downloading and uncompressing jena-fuseki-1.0.0-distribution.tar.gz (this takes a few minutes) ..."
		cmd=<<BASH
		mkdir -p vendor 
		pushd vendor
		curl -o jena-fuseki-1.0.0-distribution.tar.gz http://www.apache.org/dist/jena/binaries/jena-fuseki-1.0.0-distribution.tar.gz
		tar -xvzf jena-fuseki-1.0.0-distribution.tar.gz
		rm jena-fuseki-1.0.0-distribution.tar.gz
		popd
BASH
		sh cmd
	end
end

task :check_dependancies do
	raise RuntimeError, "vendor/jena-fuseki-1.0.0 isn't installed.  run rake fuseki:install" unless \
		File.directory?("vendor/jena-fuseki-1.0.0")
end

desc "Run all services"
task :run => :check_dependancies do
  sh "foreman start"
end
