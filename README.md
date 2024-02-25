# Jamstack Website Static Resources Overview

Large static assets for the Jamstack website should be put in this repository.

Generally speaking, this repository should contain content such as images or PDF files that are related to your Jamstack website posts.

Smaller structural files, such as your CSS and JavaScript files, can stay with your dynamic site repository (making development easier).

> [!IMPORTANT]
> Do not use this repository directly, the "Use this template" button should be utilized to create your own copy of this repository.  This will allow you to upload content specific to your website.  Though it is unlikely there will be enhancements to this repository, if there are, you can pull them in as needed.

---

## Table of Contents

- [Usage](#usage)
- [Related Repositories](#related-repositories)
- [License](#license)

---

# Usage

1. Put the large content files for your Jamstack website in the [`content`](content) directory before deploying your latest post.
2. The deployment CodePipeline from the [Jamstack Website boilerplate](https://github.com/ngamradt/boilerplate-jamstack-website) repository will deploy all the files from this repository to the site S3 bucket when your latest post is deployed.
3. Since the content files are in the `content` directory, they will be in the `content` directory in your S3 bucket.
4. If you don't want the `CONTRIBUTING.md`, `LICENSE`, and `README.md` files deployed to S3, then remove them from the repository.

> [!NOTE]
> Since these files are being deployed via CodePipeline, the maximum artifact size is a 1GB ZIP file.  If you are reaching this limit, understand that the S3 deployment process being used only adds and updates files, it also does a shallow clone from Git, so you could remove older files from the repository and they will not get removed from the S3 bucket.  So this would be a way to free up space and still use the CodePipeline deployment step.

The other option would be to deploy the resources from this repository manually to S3, but that does break the GitOps model a bit.

# Related Repositories

This repository is part of a small group of repositories that are used together in order to deploy a simple 11ty Jamstack website.  Here is the list of related repositories:

1. [Jamstack Website Core](https://github.com/ngamradt/boilerplate-jamstack-website): This repository is the core repository that stitches everything together.  It houses the following components:
    - The main AWS CodePipeline that will deploy all infrastructure and the Jamstack website itself.
    - All needed CloudFormation templates to create the required infrastructure.
    - The 11ty liquid templates for the structure of the website.
    - The supporting CSS and JavaScript files for the Jamstack site.
    - All of the source content files for each blog post.
2. [Jamstack Website Tools](https://github.com/ngamradt/boilerplate-jamstack-website-tools): This repository has any supporting tools for the Jamstack website.
3. [Jamstack Website Build](https://github.com/ngamradt/boilerplate-jamstack-website-build): This repository has the Lambda function that is used to produce the 11ty dynamic pages.
4. [Jamstack Website Static Resources](https://github.com/ngamradt/boilerplate-jamstack-website-static) (this repository): This repository has all large static files that are used either by the site in general, or by the individual posts.  These files are kept separate in order to keep the build process fast and easy.

These repositories are part of my ["Blog on a Budget" series](https://nealgamradt.com/posts/2023/06/blog-on-a-budget-overview/index.html).  View that blog post series for more details on how these repositories all work together.

# License

This repository is released under [the MIT license](https://en.wikipedia.org/wiki/MIT_License).  View the [local license file](./LICENSE).
