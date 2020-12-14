<template>
<input type="button" value="Сортувати за автором" @click="sortPhotosByAuthor"/>
<input type="button" value="Сортувати за датою" @click="sortPhotosByDate"/>
<ul class="block">
  <li v-for="(photo, i) in photos" :key="i" class="blockEl"> 
      <h1>{{photo.Name}}</h1>
      <h3>Автор:{{photo.Author}}</h3>
      <p>Опис зробленого фото:{{photo.Description}}</p>
      <img alt="Cover" :src="photo.UrlFile" class="photoClass"/>
      <p>Дата:{{photo.DateofPublishing}}</p>
      <span>Кількість вподобань:{{photo.NumberofLikes}}</span>
      <br>
     Hashtags:
     <ul class="hashtagsStyle">
        <li v-for="hashtag in photo.Hashtags" :key="hashtag">{{hashtag}}</li>
      </ul>
      Коментарі:<br>
      <ul>
        <li v-for="comment in photo.CommentsList" :key="comment">{{comment}}</li>
      </ul>
    </li>
</ul>
</template>
<script>
export default{
    data(){
        return{
            photos:[
              {
                  Id:1,
                  Author:"Матяшовська",
                  Name:"Краса",
                  Description:"Фото з Парижу",
                  Hashtags:["#photos","#France"],
                  DateofPublishing:new Date('2020-07-15'),
                  UrlFile:"https://www.planetware.com/wpimages/2020/02/france-in-pictures-beautiful-places-to-photograph-eiffel-tower.jpg",
                  NumberofLikes:23,
                  CommentsList:["Як гарно","Яка ж ти везуча, так попасти в Париж!!!!"]
              },
              {
                  Id:2,
                  Author:"Кампо",
                  Name:"Моя Мая",
                  Description:"домашній улюбленець Віки",
                  Hashtags:["#photos","#kitties"],
                  DateofPublishing:new Date('2020-07-28'),
                  UrlFile:"https://icatcare.org/app/uploads/2018/07/Thinking-of-getting-a-cat.png",
                  NumberofLikes:100,
                  CommentsList:["Яка гарнюня!!!","дуже гарна кішка","Бaчу,ти її дуже любиш"]
              },
              {
                  Id:3,
                  Author:"Опіярі",
                  Name:"Машина мрії",
                  Description:"Зображення автомобіля",
                  Hashtags:["#photos","#cars"],
                  DateofPublishing:new Date('2020-06-28'),
                  UrlFile:"https://auto.ironhorse.ru/wp-content/uploads/2020/03/S8-D5-tmb-550x300.jpg",
                  NumberofLikes:43,
                  CommentsList:["це просто бомба!!!","на таку працювати і працювати..."]
              },
            ]
        }
    },
    methods:
    {
      sortPhotosByAuthor()
    {
      this.photos.sort((photo1, photo2) =>  photo1.Author>photo2.Author ? 1 : -1);
    },
    sortPhotosByDate()
    {
           this.photos.sort((photo1, photo2) => photo1.DateofPublishing > photo2.DateofPublishing ? 1 : -1);
    }
  }
}
</script>
<style scoped>
body{
    position:relative;
}
.hashtagsStyle{
    display:flex;
    list-style-type:none;
    color:blue;
}
.photoClass{
    height:300px;
    width:300px;
}
.block{
    
    list-style-type:none;
    position:absolute;
}
.blockEl{
    background-color:#FFBE33;
    position:relative;
    float:left;
    width:350px;
    margin:5px;
    height:700px;
}
</style>