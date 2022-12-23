require 'html-proofer'

task default: [:build, :test]

task :build do
  system('bundle exec jekyll build')
end

task :test do
  htmlproofer_options = {
    ignore_status_codes: [403, 404, 429, 999],
    typhoeus: {
      ssl_verifypeer: false,
      ssl_verifyhost: 0
    }
  }

  HTMLProofer.check_directory('_site', htmlproofer_options).run
end
