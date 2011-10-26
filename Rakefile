namespace :build do
  directory '_layouts'
  directory '_posts'
  directory '_includes'
  directory '_site'
  directory 'css'
  directory 'images'

  file 'config' do touch '_config.yml' end 
  file 'index' do touch 'index.html' end
  file 'default' do touch '_layouts/default.html' end
  file 'post' do touch '_layouts/post.html' end

  desc "Builds basic Jekyll file structure"
  task :all => ['_layouts', '_posts', '_includes', '_site', 'css', 'images', 'index', 'config', 'default', 'post']
end

desc "Given a title as an argument, create a new post file"
task :write, [:title, :category] do |t, args|
  filename = "#{Time.now.strftime('%Y-%m-%d')}-#{args.title.gsub(/\s/, '_').downcase}.markdown"
  path = File.join("_posts", filename)
  if File.exist? path; raise RuntimeError.new("Won't clobber #{path}"); end
  File.open(path, 'w') do |file|
    file.write <<-EOS
---
layout: post
category: #{args.category}
title: #{args.title}
date: #{Time.now.strftime('%Y-%m-%d %k:%M:%S')}
---
EOS
    end
    puts "Now open #{path} in an editor."
end

# http://bit.ly/hNUaAH
namespace :minify do
  desc 'Merge all'
    task :all do
      Rake::Task[:css].invoke
      Rake::Task[:js].invoke
    end

  desc 'Merges stylesheets'
    task :css => :"juicer:js" do
      sh 'juicer merge --force _site/style/master.css'
    end
  desc 'Merges JavaScripts'
    task :js do
      sh  'juicer merge -i --force _site/js/master.js'
    end
end
