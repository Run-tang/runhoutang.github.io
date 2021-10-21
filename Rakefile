require 'fileutils'
require 'html-proofer'

task :test do
  FileUtils.rm_rf('./_site')
  sh "bundle exec jekyll build --config _config.yml"
  HTMLProofer.check_directory("./_site", {
    :allow_hash_href => true,
    :check_html => true,
    :file_ignore => ["docker.sh"],
    :url_ignore => []
    }).run
end
