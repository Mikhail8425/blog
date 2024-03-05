01  cmd rails new blog
02  cmd bin/rails server -b 0.0.0.0
03  config/routes.rb get "/articles", to: "articles#index"
04  cmd bin/rails generate controller Articles index --skip-routes
05  app/views/articles/index.html.erb <h1>Hello, Rails!</h1>