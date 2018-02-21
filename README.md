# instructions-on-rails

1. type rails new "project name" in terminal


2. cd into project folder


3. open file in sublime


4. type rails g controller "name of controller"


5. type rails g model "name of model" (singular)
6. open your controller you just made and make functions for all the crud steps: Index, New, Create, Show, Edit, Update, Destroy, list strong params: def blog_params for ex.  params.require(:blog).permit(:title, :content)


7. go to db folder and open the table for new migration, populate the table with the t.string lists


8. go to terminal and type rake db:migrate


9. go to rails s and make a blog


10. go to config folder and open routes.rb.  Type in your resources command: resources :blog

11. go to terminal and type in rails routes to see all the routes of the url of the project.

12. go to your controller and start performing crud.  INDEX: @blog = Blog.all

13.  Go to views and make new file: index.html.erb.  Go to page and make an <h2> tag with some words.  Next is the embedded ruby <% blogs.each do |b| %>
list your b.title and b.content in embedded ruby lines with an end statement

14. Go to routes.rb and make your home page route: root to: "blogs#index". Up to us which page will be home page.

15. go to controller and for new and create steps you need a form.  Go to views make a new file for new.html.erb.

16.  Go to new view file and create the form for the new blog.  <%= form_for @blog do |f| %>
<div><%= f.text_field :title %></div>
<div><%= f.text_area :content %></div>
  <%= f.submit %>
<% end %>

17. go to the controller and define the @blog variable under the def new function. @blog = Blog.new

18. Create a New Blog: in the controller in the create function: blog = Blog.new(blog_params); strong parameter.  If save then redirect to home, else render '/blogs/new'.Need end for the if statement.

19. Flash Messages: In the views folder, open layouts.  open application.html.erb.  type in your flash syntax in the body.  This makes it available on every page.

20. go to the function that you want the flash message to appear on and type flash[:message] = "my message to the user".

21. back to the controller, define the show function: @blog = Blog.find(params[:id]).

22. go to views and make your new show.html.erb page.  Type your embedded ruby: <div><%= @blog.title %></div>
<div><%= @blog.content %></div>
This shows the blogs only for the targeted blog id

23. go to views and create the edit.html.erb so you can input a form. <%= form_for @blog do |f| %>
<div><%= f.text_field :title %></div>
<div><%= f.text_area :content %></div>
  <%= f.submit %>
<% end %>

24. go back to the controller and define the edit function: @blog = Blog.find(params[:id]

25.  define update as well since edit/update are similar.  @blog = Blog.find(params[:id]).
if blog.update(blog_params)
flash[:message] = "your message to user"
redirect_to '/blogs/#{blog.id}/'
else render "/blogs/#{blog.id}/edit"

must have double quote when using interpolation.  Wont work with single quotes.

26. make a nav bar  in the applications.erb in the layouts.

27. The destroy method, go to the page you wish to display the delete button.  write the embedded ruby:

<%= link_to 'Destroy', blog_path, method: :delete %>

link_to connects you to the different pages within your app.  Your rails routes command in terminal you can see what paths lead you to where in your app.

28. go to the controller and define the destroy function: @blog = Blog.find(params[:id])
@blog.destroy
redirect_to root_path or redirect '/'

29. BCRYPT - protects the password.
go to Gemfile of your app.  Uncomment the line that has the BCRYPT gem.
go to terminal and run bundle install to access the gem

30. back in terminal, type rails g controller users index new show.  Giving the crus actions I want to include in my controller for users

31. in terminal rails g model User

32. check out the migration for user in the db folder.  Populate the table with the t.string commands.

must put the _digest syntax after the :password t.string command for BCRYPT to take effect.
