01  cmd rails new blog
02  cmd bin/rails server -b 0.0.0.0
03  config/routes.rb get "/articles", to: "articles#index"
04  cmd bin/rails generate controller Articles index --skip-routes
05  app/views/articles/index.html.erb <h1>Hello, Rails!</h1>
06  config/routes.rb root "articles#index" get "/" dispalys index page 
07  cmd bin/rails generate model Article title:string body:text
08  cmd bin/rails db:migrate
09  cmd bin/rails console 
10  irb> article = Article.new(title: "Hello Rails", body: "I am on Rails!")
11  irb> article.save
12  irb> article
13  irb> Article.find(1)
14  irb> Article.all