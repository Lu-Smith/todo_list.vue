<template>
  <footer>Coded by <a href="https://www.lunasmithart.com/" target="_blank">Luna Smith</a>, open-sourced on 
  <a href="https://github.com/Lu-Smith/todo_list.vue" target="_blank">GitHub</a>.</footer>
</template>

<style>
footer {
    position: fixed;
    bottom: 0;
    right: 0;
    left: 0;
    text-align: center;
    background-color: #f2f2f2;
    padding: 20px;

}

footer a {
  color: #333;
  text-decoration: none;
  position: relative;
  transition: color 0.3s;
}

footer a::before {
  content: "";
  position: absolute;
  width: 100%;
  height: 2px;
  bottom: -5px;
  left: 0;
  background-color: #333;
  visibility: hidden;
  transform: scaleX(0);
  transition: all 0.3s ease-in-out;
}

footer a:hover {
  color: #d17c37;
}

footer a:hover::before {
  visibility: visible;
  transform: scaleX(1);
}


</style>