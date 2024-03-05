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
15  app/controllers/articles_controller.rb @articles = Article.all
16  app/views/articles/index.html.erb 
  <h1>Articles</h1>
  <ul>
    <% @articles.each do |article| %>
      <li>
        <%= article.title %>
      </li>
    <% end %>
  </ul> /=> displays articles from db
17 config/routes.rb get "/articles/:id", to: "articles#show"
18  articles_controller.rb 
  def show
    @article = Article.find(params[:id])
  end
19 views create show.html.erb 
  <h1><%= @article.title %></h1>

  <p><%= @article.body %></p>
20 index.html.erb update to <h1>Articles</h1>

  <ul>
    <% @articles.each do |article| %>
      <li>
        <a href="/articles/<%= article.id %>">
          <%= article.title %>
        </a>
      </li>
    <% end %>
  </ul>
21  routes.rb update to 
  root "articles#index"
  resources :articles
22  update index.html.rb
  <ul>
    <% @articles.each do |article| %>
      <li>
        <%= link_to article.title, article %>
      </li>
    <% end %>
  </ul>
23  articles_controller.rb add:
  def new
    @article = Article.new
  end

  def create
    @article = Article.new(title: "...", body: "...")

    if @article.save
      redirect_to @article
    else
      render :new, status: :unprocessable_entity
    end
  end
24 create newhtmk.erb with following code 
  <h1>New Article</h1>

  <%= form_with model: @article do |form| %>
    <div>
      <%= form.label :title %><br>
      <%= form.text_field :title %>
    </div>

    <div>
      <%= form.label :body %><br>
      <%= form.text_area :body %>
    </div>

    <div>
      <%= form.submit %>
    </div>
  <% end %>