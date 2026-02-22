<!DOCTYPE html>
<html>
<head>
<style>
body{
  margin:0;
  height:100vh;
  display:flex;
  justify-content:center;
  align-items:center;
  font-family:monospace;
  background:white;
}

.text{
  font-size:55px;
  border-right:3px solid black;
  white-space:nowrap;
  overflow:hidden;
}
</style>
</head>
<body>

<div class="text" id="text"></div>

<script>
const words = ["Hi", "I'm Rishav"];
let i = 0;
let j = 0;
let current = "";
let isDeleting = false;
const speed = 100;

function type(){
  if(i < words.length){
    if(!isDeleting && j <= words[i].length){
      current = words[i].substring(0,j++);
      document.getElementById("text").textContent = current;
    }

    if(j === words[i].length+1){
      setTimeout(()=> isDeleting = true, 800);
    }

    if(isDeleting && j >= 0){
      current = words[i].substring(0,j--);
      document.getElementById("text").textContent = current;
    }

    if(j < 0){
      isDeleting = false;
      i++;
    }

    setTimeout(type, speed);
  }
}

type();
</script>

</body>
</html>


## 🌐 Socials:
[![Instagram](https://img.shields.io/badge/Instagram-%23E4405F.svg?logo=Instagram&logoColor=white)](https://instagram.com/rishav_chambyal) [![LinkedIn](https://img.shields.io/badge/LinkedIn-%230077B5.svg?logo=linkedin&logoColor=white)](https://linkedin.com/in/rishav-rajput-213112361)[![email](https://img.shields.io/badge/Email-D14836?logo=gmail&logoColor=white)](mailto:rishavrajput204@gmail.com) 

# 💻 Tech Stack:
![C](https://img.shields.io/badge/c-%2300599C.svg?style=for-the-badge&logo=c&logoColor=white) ![Python](https://img.shields.io/badge/python-3670A0?style=for-the-badge&logo=python&logoColor=ffdd54) ![JavaScript](https://img.shields.io/badge/javascript-%23323330.svg?style=for-the-badge&logo=javascript&logoColor=%23F7DF1E) ![Java](https://img.shields.io/badge/java-%23ED8B00.svg?style=for-the-badge&logo=openjdk&logoColor=white) ![HTML5](https://img.shields.io/badge/html5-%23E34F26.svg?style=for-the-badge&logo=html5&logoColor=white) ![CSS3](https://img.shields.io/badge/css3-%231572B6.svg?style=for-the-badge&logo=css3&logoColor=white) ![C++](https://img.shields.io/badge/c++-%2300599C.svg?style=for-the-badge&logo=c%2B%2B&logoColor=white) ![AWS](https://img.shields.io/badge/AWS-%23FF9900.svg?style=for-the-badge&logo=amazon-aws&logoColor=white) ![Apache Maven](https://img.shields.io/badge/Apache%20Maven-C71A36?style=for-the-badge&logo=Apache%20Maven&logoColor=white) ![Apache Tomcat](https://img.shields.io/badge/apache%20tomcat-%23F8DC75.svg?style=for-the-badge&logo=apache-tomcat&logoColor=black) ![Jenkins](https://img.shields.io/badge/jenkins-%232C5263.svg?style=for-the-badge&logo=jenkins&logoColor=white) ![MySQL](https://img.shields.io/badge/mysql-4479A1.svg?style=for-the-badge&logo=mysql&logoColor=white) ![Git](https://img.shields.io/badge/git-%23F05033.svg?style=for-the-badge&logo=git&logoColor=white) ![GitHub](https://img.shields.io/badge/github-%23121011.svg?style=for-the-badge&logo=github&logoColor=white) ![Docker](https://img.shields.io/badge/docker-%230db7ed.svg?style=for-the-badge&logo=docker&logoColor=white) ![Postman](https://img.shields.io/badge/Postman-FF6C37?style=for-the-badge&logo=postman&logoColor=white)
# 📊 GitHub Stats:
![](https://github-readme-stats.vercel.app/api?username=voidirl&theme=jolly&hide_border=false&include_all_commits=true&count_private=true)<br/>
![](https://nirzak-streak-stats.vercel.app/?user=voidirl&theme=jolly&hide_border=false)<br/>
![](https://github-readme-stats.vercel.app/api/top-langs/?username=voidirl&theme=jolly&hide_border=false&include_all_commits=true&count_private=true&layout=compact)

### ✍️ Random Dev Quote
![](https://quotes-github-readme.vercel.app/api?type=horizontal&theme=dark)

---
[![](https://visitcount.itsvg.in/api?id=voidirl&icon=0&color=0)](https://visitcount.itsvg.in)

<!-- Proudly created with GPRM ( https://gprm.itsvg.in ) -->
