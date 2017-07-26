# FTP Upload with Editorial

_Captured: 2015-06-14 at 14:23 from [www.macdrifter.com](http://www.macdrifter.com/2013/08/ftp-upload-with-editorial.html)_

[Here's a workflow](http://editorial-app.appspot.com/workflow/6647441143103488/cXuFMzpjZuY) that uploads the currently open document in Editorial as a markdown file to an FTP host. I use a variation of this workflow to post here on Macdrifter. In fact, this post was written and uploaded from Editorial.

Here's the detail of the Python script:
    
    
    import workflow
    import editor
    import ftplib
    import console
    import StringIO
    import keychain
    import pickle
    import cgi
    
    # Uncomment this line to reset stored password
    #keychain.delete_password('macdrifter', 'editorial')
    login = keychain.get_password('macdrifter', 'editorial')
    if login is not None:
        user, pw = pickle.loads(login)
    else:
        user, pw = console.login_alert('FTPS Login Needed', 'No login credentials found.')
        pickle_token = pickle.dumps((user, pw))
        keychain.set_password('macdrifter', 'editorial', pickle_token)
    
    #
    
    remotePath = "/home/my/full/path/"
    host = "hostname.com"
    port = 22
    
    docTitle = workflow.get_variable('postTitleVar')
    fileName = docTitle+'.md'
    confirmation = console.alert('Confirm', 'Go ahead and post?','Yes','No')
    
    postContent = editor.get_text()
    
    # Text encoidng sucks!
    encode_string = cgi.escape(postContent).encode('ascii', 'xmlcharrefreplace')
    #postContent.encode('ascii', 'replace')
    
    buffer = StringIO.StringIO(encode_string)
    #buffer.write(postContent)
    buffer.seek(0)
    
    try:
        ftp = ftplib.FTP(host, user, pw)    
        ftp.cwd(remotePath)
        ftp.storbinary('STOR '+ fileName, buffer)
        ftp.quit()
    except Exception, e:
        print e
        console.alert('Error', e)
    
    action_in = workflow.get_input()
    console.hud_alert('Posted '+fileName, 'success')
    
    # Extension point to do something after the file is uploaded
    action_out = action_in
    
    workflow.set_output(action_out)
    
