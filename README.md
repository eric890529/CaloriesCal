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
先用removefood把增加新紀錄前的食物刪除，再用callback方式call myFood(array)，把食物經由找id=myfood的方式，把資料已div標籤的方式顯示在上面。

