require 'html-proofer'

task default: [:build, :test]

task :build do
  system('bundle exec jekyll build')
end

task :test do
  htmlproofer_options = { assume_extension: true, http_status_ignore: [999] }

  HTMLProofer.check_directory('./_site', options).run
end
