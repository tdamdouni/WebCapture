# Publish Jekyll Post

_Captured: 2015-09-26 at 10:03 from [www.editorial-workflows.com](http://www.editorial-workflows.com/workflow/5838419494174720/XyeFJfsyXwE)_

[App Website](http://omz-software.com/editorial) | [Contact](http://omz-software.com/contact)

[Install Workflow...](http://www.editorial-workflows.com/workflow/5838419494174720/XyeFJfsyXwE)

This is a workflow for [Editorial](http://editorial-app.com), a Markdown and plain text editor for iOS. To download it, you need to view this page on a device that has the app installed.

**Description:** Publish a Jekyll post to GitHub Pages. Not compatible with Octopress. File issues at https://github.com/maxjacobson/github-pages-editorial

**Comments:** [Comment Feed (RSS)](http://www.editorial-workflows.com/workflow/rss/5838419494174720/XyeFJfsyXwE)

There are no comments yet.

You must generate a GitHub application-specific access token and enter it in the "Configure Access Token" step of the workflow. Want to go to the page on GitHub where you can do that?

Stopping because your GitHub username or repo name are blank. Please provide them in the "Configure repo" step.

Source Code
    
    
    #coding: utf-8
    import workflow, requests, editor, base64, json
    
    post = editor.get_text()
    filename = workflow.get_variable('filename')
    path_to_repo = workflow.get_variable('path_to_repo')
    path_to_file = workflow.get_variable('path_to_file')
    access_token = workflow.get_variable('github_access_token')
    
    root = "https://api.github.com"
    endpoint = "/repos/" + path_to_repo + "/contents/" + path_to_file
    
    headers = {}
    headers['Accept'] = 'application/vnd.github.v3+json'
    headers['Authorization'] = "token " + access_token
    
    params = {}
    params['content'] = base64.b64encode(post)
    params['message'] = workflow.get_variable('commit_message')
    
    result = requests.put(root + endpoint, headers=headers, data=json.dumps(params))
    
    output = "error!!!"
    
    if result.status_code == 201:
    	output = result.json()['content']['html_url']
    
    workflow.set_output(output)
    
