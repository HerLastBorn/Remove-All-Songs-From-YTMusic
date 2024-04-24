This script will remove all songs from your YouTube Music Library by iterating through the song list, clicking the three dots, and clicking "Remove From Library" until the list is empty.

YouTube doesn't have a way to mass remove songs from the library.

You can remove all likes by clicking on your profile -> Manage Your Google Account
-> Data&Privacy -> My Activity -> Other Activity -> View Likes and Dislikes -> Delete All

You Can delete history by going to Other Activity -> (Youtube History) Manage Activity -> Delete -> Delete All Time

Doing these will clear all your likes and views, but not saved playlists or songs. I don't use playlists, so I only wrote and tested the script for songs.


***Tested in Firefox Version 125.0.2 (64-bit)***

Go to https://music.youtube.com/library/songs

press F12

click on console

in the command line, try pressing "ctrl"+"v"

if it tells you to type "allow pasting" do it

then try pasting again

if you can paste, then paste this code:
```javascript
function wait1sec() {
  return new Promise((resolve) => {
    setTimeout(() => {
      resolve('resolved');
    }, 500);
  });
}

async function remove_songs() {
  while (true){
    var item = document.querySelectorAll(".dropdown-trigger.ytmusic-menu-renderer");
    if (item.length == 0) {
      break
    }
    item[0].click();
    await wait1sec()
    var dropdown = document.body.querySelector(".ytmusic-menu-popup-renderer");
    var dplist = dropdown.childNodes;
    var remove_button = dplist[5];
    remove_button.click();
    console.log("song ", item.length, " removed");
    await wait1sec()
  }
  console.log("done")
}
remove_songs()
```
