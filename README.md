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
