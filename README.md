# CubariManga
Manga links for Cubari reader

# Manga Links

[Otaku no Otoku ni Gal Gurashi](/OtakuNiOtokuNaGal) : https://cubari.moe/read/gist/JuKF9/

# Tutorial
Link: https://www.reddit.com/r/manga/comments/mcicbp/sl_how_to_host_a_series_on_imgur_with_guyamoe/

# Archived Post
<details>
<summary>Click to Expand</summary>

Just wanna start off saying that this guide is for getting multiple chapters under one link for a series using [guya.moe](https://guya.moe), not just for viewing a single chapter. The devs talked about this in the mangadex discord server but no one made a guide, so I tried making one. Some parts of this guide are taken from [u/Kawaii\_Loli\_Imouto](/u/Kawaii_Loli_Imouto/)'s guide.

Uploading to Imgur

*   Before Starting make sure you have created an [imgur](https://imgur.com/) account and a [github](https://github.com/) account
    
*   Export your manga chapter to a folder somewhere (and order/zeropad the filenames properly).
    
*   Go to Imgur and hit the green "New post" button on the top left. Then hit the "Choose Photo/Video" button and navigate to the folder your images are..
    
*   A file explorer window should have popped up. Select the very last image of the chapter, hold shift, and then click on the very first image of the chapter. In the "file name" field at the bottom, you should see the file names in the correct order.
    
*   Hit "open" and wait for the files to upload. After this is done, name your gallery (and you can choose either community or hidden)
    
*   Repeat this for all the chapters you want hosted.
    

Initial Setup

*   Next go to github and press the green “New” button on the top left. Then name the repository and make sure it’s public (you can skip the “initialize this repository with:” section) and create the repository
    
*   Next, click “creating a new file” in the quick setup section. Give the file any name that you want, but make sure the name is something that you won’t change (everytime you change the name, it’ll change the url link)
    
*   In the “edit the new file” field paste this code.
    

  
```json
    {
      "title": "<manga title>",
      "description": "<manga description>",
      "artist": "<manga artist>",
      "author": "<manga author>",
      "cover": "<mangacoverurl.jpg>",
      "chapters": {
        "<chapter number>": {
          "title": "<chapter name>",
          "volume": "<volume number>",
          "groups": {
            "<group name>": "/proxy/api/imgur/chapter/<imgur id>/"
          },
          "last_updated": "1616368746"
        },
      }
    }
```

*   Then fill out every field that has <> around it. For the <imgur id> field, go to imgur and take the Imgur ID (the alphanumeric string after `imgur.com/a/` in the url) of the first chapter that you want to host and paste it. Once this is done, make sure to remove the last comma in the code and click “commit new file”
    
*   Next, go back to the file, click “raw” and then copy the url. Go to [git.io](https://git.io/), paste the url and shorten it. Copy the git id of this url (it’s the string of letters after `https://git.io/` in the url) and paste this id in `https://guya.moe/proxy/gist/<git id>/` (replace the <git id> field). This will be your permanent url for your manga series (as long as you don’t change the name of the github file.
    

Adding more chapters

*   Go back to the github code that you wrote earlier and edit it (pencil icon).
    
*   Reinsert the comma after the bracket right below “last updated”
    
*   In a new line right above the last two brackets, paste this code and change the fields to match the info of the chapter you're adding (make sure you change the imgur id to match the chapter)
    
```json
       "<chapter number>": {
          "title": "<chapter name>",
          "volume": "<volume number>",
          "groups": {
            "<group name>": "/proxy/api/imgur/chapter/<imgur id>/"
          },
          "last_updated": "1616368746"
        },
```
  

*   Repeat this for each chapter that you want to add
    
*   Once you finish with all the chapters, remove the last comma at the end of the code and click commit changes.
    
*   When you go back to your guya url, it should be updated with the new chapters.
    

If you have any errors or want it to be formatted better, copy your github code and run it through the [jsonformatter](https://jsonformatter.curiousconcept.com/#). This will automatically fix errors and tell you where they’re at. Then replace the contents of the GitHub file with the formatted json data.

Edit: If you want to add info about the time of the upload, replace "1616368746" with a unixtimestamp from [unixtimestamp.com](https://unixtimestamp.com)

Edit 2: If you want a custom git id, change the name of your github file (this is to break the old git.io id). Then copy the command below and put the raw url of the github file after "url="

Put the custom git id name you want after "code="

    curl https://git.io/ -i -F "url=<Paste Raw Url Here>" -F "code=<newgitid>"
    

Then copy the edited version of the command and paste it in Command Prompt (or Terminal on Mac + Linux). Your new git id is what you put in the "code=<new git id>". If this doesn't work, you either need to install curl for your system, or you already have a git id linked to your github file's name (which means you need to rename your github file).

Edit 3: If you have hundreds of chapters that need to be uploaded at once, you could also use Google Drive or Amazon S3 (using a [script](https://github.com/KojoZero/CubariS3JsonCreator))

Here is an example: [Bleach Colored](https://cubari.moe/read/gist/BleachColored)

</details>
