source 'https://rubygems.org'

# 与 GitHub Pages 线上环境保持一致（内含 jekyll 3.9、jekyll-paginate、jekyll-remote-theme 等）
gem 'github-pages', group: :jekyll_plugins

# Windows 时区数据
gem 'tzinfo-data', platforms: [:mingw, :mswin, :x64_mingw, :jruby]

# 说明：Windows 上不再强制安装 wdm（它需要 DevKit 编译，容易导致 bundle install 失败）。
# Jekyll 会自动退化为轮询监听，本地预览不受影响。

# Ruby 3.0+ 不再内置 webrick，避免 `bundle exec jekyll serve` 启动报错
gem "webrick", "~> 1.8"
