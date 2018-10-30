require 'html-proofer'

task default: [:build, :test]

task :build do
  system('bundle exec jekyll build')
end

task :test do
  htmlproofer_options = {
    assume_extension: true,
    http_status_ignore: [401, 999],
    typhoeus: {
      ssl_verifypeer: false,
      ssl_verifyhost: 0
    }
  }

  HTMLProofer.check_directory('_site', htmlproofer_options).run
end
