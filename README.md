Steps to create this project:
1. `rails new turbobug -T -a propshaft -j esbuild`
2. `rails g scaffold post title`
3. `rails db:migrate`
4. Add `validates :title, presence: true` to `app/models/post.rb`
5. Change redirect after post creation to `posts_url` instead  `post_url`:
    - Before `redirect_to post_url(@post), notice: "Post was successfully created."`
    - After: `redirect_to posts_url, notice: "Post was successfully created."`
    - Ps.: This step is optional, the bug can be reproduced without this but you have to navigate back to posts list after creating a post.
6. Visit `http://localhost:3000/posts`
# Steps to reproduce the bug

1. Visit http://localhost:3000/posts
2. Click "New post".
3. Submit without filling title input. The error will be shown
4. Click on "Back to posts" link
5. Click "New post".
6. The error from step 3. will flash on screen and then will disappear <== BUG HERE
