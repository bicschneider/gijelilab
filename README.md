#Continuous Delivery & DevOps conference Oslo 2015

__GiJeLi Pages for www.code-conf.com/osl15__

The site is designed to be a sub site to www.code-conf.com hosted from a subdirectory named `osl15`.

The site is hosted by Github pages as a project (sub) site, therfore the live branch is `gh-pages` and not `master`. This is by convention, study the difference between [project sites and user/organisation sites](https://help.github.com/articles/user-organization-and-project-pages/) if your curious about the details.

To serve a jekyll site you fire it up with a `baseurl` setting as a parameter when you start the server:

    jekyll serve --baseurl /osl15 --watch

Use this approach when you are testing locally. Don't fall for the trick and set this setting permanently in your `_config.yml` since this is also read and applied by Github pages but we're already hosting is as a project (sub) page so it will end up double as www.code-conf.com/osl15/osl15 - which is crab.

To mimic the `baseurl` without actually setting it in the `_config.yml` we have introduced another variable of our own called `root`. So our `_config.yml` contains:

    root: /osl15

__Remember__ to use this variable as a prefix to all your file references. An example: If you have an image located in `/images/my.pgn` and you want to include it use:

    ![My beautiful pic]({{site.root}}/images/my.png)
   
Or if you want to link to a internal site at `/speakers/lars+kruse.html` you should use the same approach:

    [Lars Kruse]({{site.root}}/speakers/lars+kruse.html)
    
Please not that this `{{site.root}}` prefix is required everywhere you wan't the references to be self contained within this repository - if you omit it you'll be referring to the actual domain site root - which in our case is www.code-conf.com. So any reference used _without_ `{{site.root}}` prefix will be looked up in the Git repo serving the site root. That repo is  [CoDeConf/CoDeConf.github.io](https://github.com/CoDeConf/CoDeConf.github.io).

To test that you have used this approach consistently simply serve your site form the site root when you fire it up, as demonstrated earlier. If anything is broken you will see it.

