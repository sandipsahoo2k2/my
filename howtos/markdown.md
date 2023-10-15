# Different types of links/texts markdown formats that you can use while publishing your content with us
Interviewdose.com supports a wide range of Markdown formats, including those commonly used on platforms like GitHub. While it's designed to handle a variety of Markdown styles, it may also be compatible with additional formats not specifically mentioned here.  

Here in this example all most all types of types of links, text that can be used in a markdown file is listed. You can refer this as your markdown manual for writing/editing any github markdown file that can be shared with us.

Sharing is caring, Happy writing :)

## Different types of links

- [Section 1 in this file](#section-1)
- [Section 2 in this file](#section-2)

[This file is at the root level as the README.md](file2.md)
  - link pointing to a file in the root level
    
[This file resides in the /hubby folder](/hubby/projects.md)
  - Link pointing to a file inside folder
    
[This file resides in the /hubby/math folder](./hubby/math/list1.md)
  - Link pointing to a file inside nested folder
    
### External links
These are the links which are fully qualified domains 
which are outside of your domain.
- This is a link which doesn't need any formatting https://google.com
- This is a hyper link which has different text than it's actual link [Click here](https://google.com)
- This is a hyper link which <a href="https://google.com" target="_blank">opens in a new tab</a>
  - Github opens in the same page but once you see in our website it takes to a new tab
    
## Links for media
Here is an example for a default thumbnail by youtube for a video.  
![Added a default thumbnail image by youtube as an example](https://img.youtube.com/vi/Pz0CbXA4mn8/default.jpg)
  
### Embed youtube links
You can take one of the two below approach to add a youtube link to your content. 
- Copy the <youtubeId> and use <embed> url. Using embed and target _blank users won't go out of the website e.g
  - <a href="https://youtube.com/embed/HvMc-ECHTWk" target="_blank">Standard way of adding a youtube embed link</a>
- Youtube provides different types of thumbnails for a video, use one of them to be used to link to the video e.g
  - [![Added a hqdefault thumbnail image by youtube to link to the youtube](https://img.youtube.com/vi/Pz0CbXA4mn8/hqdefault.jpg)](https://youtube.com/embed/Pz0CbXA4mn8)

### Section 1
Look at the extra # Section 1 and space after #. Link in bracket starts with an anchor (#) and all the spaces are replaced with -  
Some content for Section 1

#### Section 2
Look at the extra # for Section 2 and space after #. Link in bracket starts with an anchor (#) and all the spaces are replaced with -  
Some content for Section 2
