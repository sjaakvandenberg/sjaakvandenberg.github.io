# Workflow

Tools used are `hexo` with several plugins, `imagemin` for image minification on a directory basis and git for uploading.

| Command                              | Description                          |
|--------------------------------------|--------------------------------------|
| `hexo clean`                         | remove ./public                      |
| `hexo generate`                      | generate ./public                    |
| `hexo new draft <post title>`        | create new draft in ./source/_drafts'|
| `hexo publish <post-title>`          | move draft to ./source/_posts/       |
| `hexo new <post title>`              | create new post in ./source/_posts/  |
| `hexo new page <page title>`         | create new page in ./source/         |
| `cd <images dir>`                    | change to images directory           |
| `imagemin * . -o 5`                  | minify images w/ optimizationLevel 5 |
| `hexo deploy`                        | deploy ./public/* to github          |

# Source Directory

| Command                              | Description                          |
|--------------------------------------|--------------------------------------|
| `git checkout source`                | change to `source` branch            |
| `git add *`                          | add files to git                     |
| `git commit -am "message"`           | commit files to git                  |
| `git push -u origin source`          | push files to `source` branch        |
