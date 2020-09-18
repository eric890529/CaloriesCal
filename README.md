# CaloriesCal 
## home.html 
首頁，用來連接到登入畫面

## signin.html signup.html
因為沒有後端，目前只做好了全螢幕的排版

## index.html
### 今日攝取
用showTodayData(array)，先抓變數record假資料，先判別是哪一餐(b,l,d,o)分別存到bfood,lfood,dfood,ofood，再用addMealChild((meal, tag, id) addFoodChild(array, tag, id)，將早餐、午餐、晚餐、其他和吃了哪些食物，利用找id=food的方式把字加上去。

### 新增食物
用addfood(array)，先創好newfood變數來存輸入的食物，再用checkCalories、checkfood變數來存輸入食物的熱量和食物，經過heckAddForm(calories, food)檢查，如果是合法字元，即加入倒array裡面
```
 var newfood =
            [
                array[array.length - 1][0] + 1,
                document.getElementById('fname').value,
                parseInt(document.getElementById('fCalories').value, 10),
            ]
```
### 我的食物
先用removefood(array, callback, id)把增加新紀錄前的食物刪除，不然會出現重複的食物疊起來，再用callback方式call myFood(array)，把食物經由找id=myfood的方式，把資料已div標籤的方式顯示在上面。

### 新增紀錄
> 點擊我的紀錄時，會先把選meal的選單隱藏起來，再用removefood(array, callback, id)把增加新紀錄前的食物刪除，不然會出現重複的食物疊起來。
```
$("#MyRecord").click(function () {
            //設定預設版面
            document.getElementById("choosemeal").style.display = "none";
            tablinks = document.getElementsByClassName("meal");
            for (i = 0; i < tablinks.length; i++) {
                tablinks[i].className = tablinks[i].className.replace(" active", "");
            }
            var activeB = document.getElementById("早餐").className += " active"

            removefood(data, showFood, "myrecord");
        })
```

然後callback showFood(array)呼叫addRecordChild(array, "div", "myrecord")，把現在有得食物顯示出來，且在每個食物的div tag裡面設定好她的value=fid跟id=食物名稱。//沒用上面的myFood(array)是因為要插入到的tag標籤不同，而且還要設定onclick，當選擇食物時，要讓選哪一餐的選單顯示出來。  
選好食物、meal後，按下submit時會開始跑下面的function，藉由class的名稱找到目前avtive德食物，抓到他的fid，meal同上，date預設值會是當日日期
這邊就可以回傳fid meal date到後端!
```
$("#submit").click(function () {
            var foodid = document.getElementsByClassName("record active")
            var fId = foodid[0].value
            
            var choosemeal = document.getElementsByClassName("meal active")
            meal = choosemeal[0].getAttribute("value")
            
            var x = document.getElementById("myDate");
            var date = x.value;
            alert("成功新增紀錄")
        });
```
```
*$.post("/signup",
                {
                   // "token": token,
                    "fId": fId,
                    "meal": meal,
                    "data":data
                },
```

