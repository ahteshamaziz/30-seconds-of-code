---
title: autoReload
tags: browser,beginner
firstSeen: 2021-09-03T19:21:15+02:00
lastUpdated: 2021-09-03T19:21:15+02:00
---

Auto reload your apis in web browser.

- Use `DOM`, `change`, `click` and `addEventListener` to change selector or click buttons.

```html
  <button type="button" class="btn btn-light" id="playbtn"><i class="fa fa-play"></i></button>
  <button type="button" class="btn btn-light" id="pausebtn"><i class="fa fa-pause"></i></button>



    <div class="col-lg-6 col-md-6 col-sm-12 m0 col-xs-12">
        <div class="select-time">
            <select class="select-menu" name="time" id="time">
                <option value="1000">1 Sec</option>  
                <option value="2000">2 Sec</option>    
                <option value="3000">3 Sec</option>    
            </select>
        </div>
    </div>
```

```js
            let timmer;
            let time = 1000;
            $(function() {
                $('#time').on('change', function(e) {
                    select_val = $(this).val();
                    time = parseInt(select_val,10);
                    clearInterval(timmer);

                });
            });

            const fetchapi = async () => {
                fetch('https://jsonplaceholder.typicode.com/todos/1')
                .then(response => response.json())
                .then(json => console.log(json))
            }

            const play = async () =>{
            timmer = setInterval(function(){ 
                fetchapi();
            }, time);
            }

            const pause = async () =>{
                clearInterval(timmer);
            }

            document.getElementById("playbtn").addEventListener("click", play);
            document.getElementById("pausebtn").addEventListener("click", pause);
  
```
