# Local Freshdesk Help Center

Back your Freshdesk Help Center in git. Modify articles locally, and deploy
directly to Freshdesk.

Goals of this project:

- Back Help Center locally (via git), not Freshdesk
- Give revision control of articles
- Reviewing article edits/changes made simpler
- Platform flexibility to be able to switch away from Freshdesk

**Note: Images will be backed by Amazon S3 so you will need an AWS account
for the images to no longer be owned by Freshdesk. Otherwise, you can leave
images backed on Freshdesk and comment out all scripts that involve S3.**

## Prerequisites

- Python 2.7
- Install necessary modules by running this the first time:

		python scripts/setup.py

- Add environment variables: 
    - Cloudfront URL: `FRESHDESK_CLOUDFRONT_URL`
    - Freshdesk subdomain: `FRESHDESK_DOMAIN`
	- Freshdesk agent API key: `FRESHDESK_API_KEY`
	- Freshdesk AWS bucket name: `FRESHDESK_BUCKET_NAME`
	- AWS Access Key: `AWS_ACCESS_KEY`
	- AWS Secret Key: `AWS_SECRET_KEY`

## Tracking Changes

Before locally editing articles and images, **always run `track-changes.py`**.
This allows for local viewing of content. All local content is available in the
"out" folder. To quit `track-changes.py`, type CTRL+C.

## Creating New Articles

- Run `create-new-post-shell.py` with the Freshdesk category and folder IDs as the parameters.
- Add the title to the file `title.html`.
- Open the file `index.html` and write the article.
	- For images, enter: `img src="<image_name>"` with the
      appropriate file type at the end (png, jpg, jpeg, gif).
	- For links to other articles, enter: `a href="<article_id>"` with the ID
      of the article you want to link to inserted.

## Local Viewing

- Ensure `track-changes.py` is running. If it wasn't, run it now.
- Once the article is complete, open the version of the article in the "out"
  folder for local viewing. This will provide a basic HTML view in your
  preferred browser.

## Deployment

- When you are ready to publish your changes, you have two options:
	- To deploy a single article, run `deploy.py` with the article ID
      as the parameter.
    - To deploy all the articles, run `deploy.py` with no parameters.
- Commit all changes that you make in the "posts" folder to GitHub
to ensure revision control and allow others to review your changes.

To edit past articles, simply edit the HTML files with `track-changes.py`
running. Local edits can be viewed in the "out" folder and use `deploy.py` as
outlined above to publish the edits. The final version should also be commited to GitHub.

## License

BSD 3-Clause, see accompanying LICENSE file.
