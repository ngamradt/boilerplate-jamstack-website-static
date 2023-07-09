# Boilerplate Jamstack Website Static Resources

Large static assets for the Jamstack website should be put in this repository.

Generally speaking, this repository should contain content such as images or PDF files that are related to your Jamstack website (such as blog posts).

Smaller structural files, such as your CSS and JavaScript files, can stay with your dynamic site repository.

## Usage

1. Put the large content files for your Jamstack website in the [`content`](content) directory before deploying your latest post.
2. The deployment CodePipeline will deploy all the files from this repository to the site S3 bucket when your latest post is deployed.
3. Since the content files are in the `content` directory, they will be in the `content` directory in your S3 bucket.
4. If you don't want the `CONTRIBUTING.md`, `LICENSE`, and `README.md` files deployed to S3, then remove them from the repository.

---

**NOTE:** Since these files are being deployed via CodePipeline, the maximum artifact size is a 1GB ZIP file.  If you are reaching this limit, the S3 deployment process being used only adds and updates files, it also does a shallow clone from Git, so you could remove older files from the repository and they will not get removed from the S3 bucket.  So this would be a way to free up space and still use the CodePipeline deployment step.

The other option would be to deploy the resources from this repository manually to S3, but that does break the GitOps model a bit.

---
