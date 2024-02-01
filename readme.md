## xm-notifyjs

# Description
This is a non FiveM relateed resource and its main purpose is for web development. I made it in English class because I wanted to see if i could do it. I plan on eventually transforming it into a FiveM resource when I think its good enough.

# Installation
The only files you need from this repository is the files in `dist`, all other files are for the example site.

Step 1. Insert code block into `head` tags if not already there.
```html
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.5.1/css/all.min.css">
    <link rel="stylesheet" href="./dist/notify.css">
```

Step 2. Insert code block into top of your `body` tags.
```html
    <!--Notification Start-->
    <div class="alert _hide" id="__al">
        <span class="_icon fa-solid " id="_icon"></span>
        <span class="_title _cctn" id="_txt"></span>
        <span class="_desc _cctn" id="_dc"></span>
    </div>
    <!--Notification End-->
```

Step 3. Insert script into bottom of html file
```js
// DO NOT EDIT UNLESS YOU KNOW WHAT YOU'RE DOING
let noti = document.getElementById("__al")
let icon = document.getElementById('_icon')
let L = 0
let a = false
function Notify(title, description, type) {
    if (a) {
        //pass
    }
    else {
        a = true
        document.getElementById('_txt').innerText = `${title}`
        document.getElementById("_dc").innerText = `${description}`
        switch (type) { // I love marginal performace enhancement!
            case 'error':
                icon.classList.add('fa-circle-xmark')
                noti.style.borderLeftColor = "red"
                L = 0
                break;
            case 'info':
                icon.classList.add('fa-circle-info')
                noti.style.borderLeftColor = "blue"
                L = 1
                break;
            case 'success':
                icon.classList.add('fa-circle-check')
                noti.style.borderLeftColor = "green"
                L = 2
                break;
            default:
                icon.classList.add('fa-circle-info')
                noti.style.borderLeftColor = "orange"
                L = 1
                console.error("Notify: Invalid type - reset to default")
                break;
        }
        noti.style.display = 'block'
        noti.classList.remove('_hide')
        noti.classList.add("_show")
        setTimeout(function(){
            noti.classList.remove('_show')
            noti.classList.add('_hide')
        }, 3000)
        setTimeout(()=>{
            noti.style.display = 'none'
            switch (L) {
                case 0:
                    icon.classList.remove('fa-circle-xmark')
                    break;
                case 1: 
                    icon.classList.remove('fa-circle-info')
                    break;
                case 2: 
                    icon.classList.remove('fa-circle-check')
                    break;
                default:
                    icon.classList.remove('fa-circle-info')
                    break;
            }
            a = false
        }, 4000)
    }

}
// DO NOT EDIT UNLESS YOU KNOW WHAT YOU'RE DOING
```

Step 4. Download the `dist` folder and move it to your src folder

You should now be able to run the function `Notify()`. The parameters are (title, description, type)

types = {'error', 'info', 'success'}

# Dependencies
 - None
