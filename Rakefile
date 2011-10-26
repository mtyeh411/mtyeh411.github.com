
namespace :jekyll do
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

  task :build => ['_layouts', '_posts', '_includes', '_site', 'css', 'images', 'index', 'config', 'default', 'post', 'gemfile']
end
