## Fedora 33 Installation Notes for Successful Build
1. Clone the git repository from GitHub and clone the repository
    ```
    $ git clone git@github.com:dennis-perrone/dennis-perrone.github.io.git blog
    ```
2. Follow the Jekyll site for required packages
    * https://jekyllrb.com/docs/installation/other-linux/
    ```
    $ sudo dnf install ruby ruby-devel openssl-devel redhat-rpm-config @development-tools
    ```
3. Follow the nokogiri site for the nokogiri package
    * https://nokogiri.org/tutorials/installing_nokogiri.html 
    ```
    $ sudo dnf install zlib-devel
    ```
4. Build Jekyll site in the git repository on local machines
    ```
    $ jekyll new . --force
    ```
5. Edit the GemFile to comment out the normal Jekyll and uncomment for gh-pages
6. Run the following `bundle` commands
    ```
    $ bundle update
    $ bundle install
    ```
7. Create a local theme based on minima
    ```
    $ bundle exec jekyll build
    ```
8. Copy contents from `/usr/share/gems/gems/minima-2.5.1` into blogs root `_site`
9. Comment out minima references in `_config.yml` and in `Gemfile`
10. Modify the following entries within `_includes/footer.html` to add fields for footer. This entry goes under the email if statement.
    ```
    {%- if site.copyright -%}
    <li>&copy; {{ site.copyright }} {{ 'now' | date: "%Y" }}</li>
    {%- endif -%}
    ```
11. Add the following entries into the `_config.yml` file
    ```
    author: Dennis Perrone
    copyright: Dennis Perrone
    linkedin_username: Dennis Perrone
    ```
12. To rearrange the order of social media in `_include/footer.html`, modify `_include/social.html` and move the following line to the top of the file.
    ```
     {%- if site.linkedin_username -%}<li><a href="https://www.linkedin.com/in/{{ site.linkedin_username| cgi_escape | escape }}"><svg class="svg-icon"><use xlink:href="{{ '/assets/minima-social-icons.svg#linkedin' | relative_url }}"></u    se></svg> <span class="username">{{ site.linkedin_username| escape }}</span></a></li>{%- endif -%}
    ```
13. To create blogs based on topic, create directory in main repo. For example, `blog-business` and within that, make sure there is a `_posts` directory so Jekyll picks up on new posts. The new `blog-business` structure should be:
    ```
    blog-business
        _posts
        assets
            images
        index.md
    ```
14. Copy `_layouts/home.html` to `_layouts/home-business.html`
15. Modify the `blog-business/index.md` and make sure the entries reflect the following lines: 
    ```
    layout: home-business
    title: Business Blog
    category: Business
    ```
    * This can also list categories if multiple categories fit into the blogs topic. The `title` is what will be displayed in the main `index.md` page in the top right hand side. 
16. Edit `_layouts/home-business` to add the following line after `{%- for post in site.posts -%}`
    ```
    {%- if post.category=="business" -%}
    
    </li>
    {%- endif -%}
    ```
17. Set up the Atom RSS for specific blog topics. This is defined in the `_layouts/home-<topic>.html` file under `rss-subscribe`. Modify the `p class="rss-subscribe">subscribe <a href="{{ "/blog-<topic>/feed.xml" | relative_url }}">via RSS</a></p>`
18. Create feed.xml file in home-<topic> directory to define the RSS feed.

## WSL2 Jekyll Steps
```
$ sudo apt install ruby-full
$ sudo apt install make gcc gpp build-essential zlib1g zlib1g-dev ruby-dev dh-autoreconf
$ sudo rm -rf /usr/lib/ruby/vendor_ruby/
$ sudo gem install
$ sudo gem update
$ sudo bundle install --full-index
$ bundle update sass
```