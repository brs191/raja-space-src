# raja-space-src commit history description.

hugo new site portfolio
create "layouts/index.html"
create "content/_index.md"
hugo server

Create about page
hugo new about.md 
	- content/about.md is created based on archetypes/default.md

mkdir layouts/_default/
cp layouts/index.html layouts/_default/single.html
	- single.html defines the layouts for single pages.
	- index.html  defines the layout for Home page only.
	
Create contact, resume page
hugo new contact.md
hugo new resume.md

hugo new theme basic
mv layouts/index.html themes/basic/layouts/index.html
mv layouts/_default/single.html themes/basic/layouts/_default/single.html

config.toml 
	- theme = 'basic'
	
themes/basic/
├── LICENSE
├── archetypes
│ └── default.md
├── layouts
│ ├── 404.html
│ ├── _default
│ │ ├── baseof.html
│ │ ├── list.html
│ │ └── single.html
│ ├── index.html
│ └── partials
│
├── footer.html
│
├── head.html
│
└── header.html
├── static
│ ├── css
│ └── js
└── theme.toml


To use basic theme:
create head.html
create footer.html
create header.html

update themes/basic/layouts/index.html with 'define block'
update themes/basic/layouts/_default/single.html

To add projects:
create "archetypes/projects.md"
hugo new projects/awesomeco.md

To add List:
hugo new projects/jabberwocky.md
Add code to themes/basic/layouts/_default/list.html

Create nav.html
create "themes/basic/layouts/partials/nav.html"
add nav.html in baseof.html to be on every page.

Add custom css file
create /static/css/sytle.css
update head.html ---- <link rel="stylesheet" href="{{ "css/style.css" | relURL }}">

Add custom image file
update content/projects/awesomeco.md ---- ![alt]( /img/boat.jpg )

create Project specific layout
mkdir themes/basic/layouts/projects/
create /portfolio/themes/basic/layouts/projects/single.html

Adding content to Projects list
hugo new projects/_index.md
update content description in _index.md
update list.html with {{.Content}}

Adding meta-params to portfolio
update /portfolio/config.toml
update /themes/basic/layouts/partials/head.html
view html source of the page in the browser

Customizing the Project list
create themese/basic/layouts/projects/list.html
copy default list.html and replace <ul> with <section>

Populating Page Content using Data in Front Matter
modify portfolio/archetypes/projects.md
hugo new projects/linkitivity.md
update awesomeco.md, jabberwocky.md with new front matter
update /themes/basic/layouts/projects/single.html to use this front matter.
update /themes/basic/layouts/projects/list.html to use this front matter.

Conditionally Displaying Data
use - with else end - construct
use - if else end - construct

Using Local Data Files
Create data/socialmedia.json
create /layouts/_default/contact.html (could be created in themes as well)
Assign contact.html layout to contact.md

Pulling Data from Remote Sources
add github_url in config.toml
create /themes/basic/layouts/_default/opensource.html
Add code to get github repos list.
Create opensource.md and assign layout.
Update oss view in style.css
Add Open-Source-Software to the projects list in themes/basic/layout/projects/list.html.

Adding a Blog
create archetypes/posts.md
hugo new posts/first-post.md
Add some text in first-post.md
Add Blog to nav.html

Create Post's Layout
create themes/basic/layouts/posts/single.html
Add Author, Posted Date and Time to Read

Organizing Content with Taxonomies
Add categories, tags in archetypes/posts.md
create themes/basic/layouts/_default/tag.terms.html
hugo new tags/_index.md
Update themes/basic/layouts/posts/single.html
update style.css for a.tag

Customizing URL & Blog List Page, 
hugo new posts/second-post.md
hugo new posts/third-post.md
hugo new posts/forth-post.md
Update config.toml
Add year,month in content/posts/first-post.md
create themes/basic/layouts/partials/post_summary.html
create themes/basic/layouts/posts/list.html
create themes/basic/layouts/_default/year.html & month.html

Fix footer to the bottom of the page
update style.css for footer

Adding Pagination
create themes/basic/layouts/posts/list_with_pagination.html
replace posts/list.html with list_with_pagination.html
update style.css for paginator
Create Paginate in config.toml

Adding Comments to Posts Using Disqus
Create account in Disqus
Take free membership and complete site setup.
Update config.toml with disqusShortname
update themes/basic/layouts/posts/single.html
Use tunneling service to test disqus

Displaying Related Content
Add keywords tag to jabberwocky.md
Add keywords tag to second-post.md
update themes/basic/layouts/posts/single.html to add Related pages.

Adding Search to Your Site
create themes/basic/layouts/search.json
hugo new search.md
all data is stored to a single file- localhost:1313/search/index.json

creating the search interface
create themes/basic/layouts/_default/search.html
add lunr,axios js scripts to search.html
cerate themes/basic/static/js/search.js

Improving search
update search.js to add regex search.
add "require all words" in search.html

Managing Stylesheets
mkdir themes/basic/assets
mv themes/basic/static/css themes/basic/assets
update head.html to take css from asset.

Using sass
rename themes/basic/assets/css/style.css to css/style.scss
create themes/basic/assets/css/_navbar.scss
copy nav code from style.scss to navbar.scss
import navbar

managing images
add hugo svg to footer

using page bundles to organize content
using figure in .md

using page bundles to organize content - shortcodes
mkdir themes/basic/layouts/shortcodes
create themes/basic/layouts/shortcodes/postimage.html
add postimages to posts/my-vacation/index.md

Bundling JavaScript files
mv themes/basic/static/js themes/basic/assets/js
download lunr.js, axios.js
update search.html

using npm with hugo
create package.json
npm run build
npm run hugo-server

using webpack with hugo
npm install --save-dev webpack webpack-cli
create webpack.config.js
mv themes/basic/assets/js/search.js themes/basic/assets/js/index.js
npm,webpack changes

Deploy the site with netlify
