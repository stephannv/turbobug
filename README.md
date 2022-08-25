Steps to create this project:
1. `rails new turbobug -T -a propshaft -j esbuild`
2. `rails g scaffold post title`
3. Add `validates :title, presence: true` to `app/models/post.rb`
4. Change redirect after post creation to `posts_url` instead  `post_url`:
    - Before `redirect_to post_url(@post), notice: "Post was successfully created."`
    - After: `redirect_to posts_url, notice: "Post was successfully created."`
    - Ps.: This step is optional, the bug can be reproduced without this but you have to navigate back to posts list after creating a post.

# Steps to reproduce the bug

1. Visits https://localhost:3000
2. Click "New post".
3. Submit without filling title input. The error will be shown
4. Fill title and submit. You be redirected to posts list
5. Click "New post".
6. The error from step 3. will flash on screen and then will disappear <== BUG HERE
