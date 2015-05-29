# Workflow

Tools used are `hexo` with several plugins, `imagemin` for image minification on a directory basis and git for uploading.

`hexo clean`                            remove ./public
`hexo generate`                         generate ./public

`hexo new <post title>`                 create new post in ./source/_posts/
`hexo new page <page title>`            create new page in ./source/

`cd <images dir>`                       change to images directory
`imagemin * . -o 5`                     minify images with optimizationLevel 5

`git add *`                             add all files
`git status`                            display git status
`git commit -a -m "Commit message"`     commit them
`git push -u origin master`             push them