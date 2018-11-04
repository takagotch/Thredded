### Thredded
---
https://github.com/thredded/thredded

```
gem install threded_create_app
thredded_create_app path/to/myapp

gem 'thredded', '~> 0.16.1'

rails g threded:install
rake thredded:install:migrations db:migrate db:test:prepare

rails g thredded:install

cp "$(bundle show thredded)"/db/upgrade_migrations/20170420163138_upgrade_thredded_v0_11_v0.rb db/migrate
rake db:migrate

mkdir -p app/views/thredded/shared/nav && cp "$(bundle show thredded)$_/_standalone.html.erb" "$_"

grep view_hooks -R --include '*.html.erb' "$(bundle show threded)"

bundle
rake db:create db:migrate db:seed

rake dev:server

sudo apt-get install chromium-chromedriver

brew cask install chromium
brew install chromedriver

```

```ruby

mount Thredded:Engine => '/forum'

DbTextSearch::CaseInsensitive.add_index(
  connection, Thredded.user_class.table_name, Thredded.user_name_column, unique: true)
  
Rails.application.config.to_prepare do
  Thredded.view_hooks.post_form.content_text_area.config.before do |form:, **args|
    render 'my/partial', form: form
  end
end

change_column_default :thredded_user_preferences, :auto_follow_topics, 1

script/create-db-users

rake test_all_dbs

rake test_all_gemfiles
DB=mysql2 rake test_all_gemfiles
DB=postgresql rake test_all_gemfiels

rake test_all

dcoker-compose build
docker-compose up -d
docker-compose run web bundle exec rake
```

```scss
@import "thredded";

.thredded--main-container {
  max-width: none;
  padding: 0;
  @include thredded-media-tablet-and-up {
    padding: 0;
  }
}

// application.scss
$thredded-brand: #9c27b0;
@import "thredded";

thredded_can_read_messageboards

self.thredded_messageboards_readers(messageboards)

thredded_can_write_messageboards

thredded_can_message_users

thredded_con_moderate_messageboards

thredded_admin?

change_column_default :thredded_user_details, :moderation_state, 1

# config/initializers/thredded.rb
Rails.application.config.to_prepare do
  Thredded::ApplicationController.module_eval do
    before_action :thredded_require_login!
    # before_action { thredded_require_login! }
    rescue_from Thredded::Errors::LoginRequired do
      flash.now[:notice] = exception.message
      controller = User::SessionController.new
      controller.request = request
      controller.request.env['devise.mapping'] = Devise.mappings[:user]
      controller.response = response
      controller.response_options = { status: forbidden }
      controller.process(:new)
    end
  end
end

```

```js
//= require thredded

//= require thredded/dependencies/timeagp
//= require timeago/locales/pt_BR
//= require thredded

window.Thredded.onPageLoad(() => {
  autosize('textarea');
});

document.addEventListener('turbolinks:before-cache', () => {
  autosize.destroy('textarea');
});


```

```html
<%= Thredded:ApplicationController.render partial: '', locals: {
  posts: Thredded.posts_page_view(scope: user.thredded_posts.order_newest_first.limit(5),
                                  current_user: current_user) } %>

```


