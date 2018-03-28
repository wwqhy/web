<template lang="html">
  <div class="index">
    <div id="wrapper">
      <img src="../assets/touxiang.jpg" id="logo">
      <h1>个人博客</h1>
      <h2>I know that my future is not just a dream.</h2>
      <button class="btn"><router-link to="/blog">进入Blog</router-link></button>
    </div>
    <canvas width="1920" height="950"></canvas>
  </div>
</template>

<script>
export default {
  mounted () {
    var c = document.getElementsByTagName('canvas')[0],
      x = c.getContext('2d'),
      pr = window.devicePixelRatio || 1,
      w = window.innerWidth,
      h = window.innerHeight,
      f = 90,
      q,
      m = Math,
      r = 0,
      u = m.PI * 2,
      v = m.cos,
      z = m.random
    c.width = w * pr
    c.height = h * pr
    x.scale(pr, pr)
    x.globalAlpha = 0.6

    function i() {
      x.clearRect(0, 0, w, h)
      q = [{
        x: 0,
        y: h * .7 + f
      }, {
        x: 0,
        y: h * .7 - f
      }]
      while (q[1].x < w + f) d(q[0], q[1])
    }

    function d(i, j) {
      x.beginPath()
      x.moveTo(i.x, i.y)
      x.lineTo(j.x, j.y)
      var k = j.x + (z() * 2 - 0.25) * f,
        n = y(j.y)
      x.lineTo(k, n)
      x.closePath()
      r -= u / -50
      x.fillStyle = '#' + (v(r) * 127 + 128 << 16 | v(r + u / 3) * 127 + 128 << 8 | v(r + u / 3 * 2) * 127 + 128).toString(16)
      x.fill()
      q[0] = q[1]
      q[1] = {
        x: k,
        y: n
      }
    }

    function y(p) {
      var t = p + (z() * 2 - 1.1) * f
      return (t > h || t < 0) ? y(p) : t
    }
    document.onclick = i
    document.ontouchstart = i
    i()
  }
}
</script>

<style media="screen" scoped>
  .index{
    font-family: 'Open Sans', 'Helvetica Neue',
    'Hiragino Sans GB', 'LiHei Pro', Arial, sans-serif;
    color: #333;
  }
  #wrapper {
    position: absolute;
    left: 0;
    width: 320px;
    text-align: center;
    top: 40%;
    left: 50%;
    margin-left: -160px;
    margin-top: -160px;
    -webkit-user-select: none;
    -moz-user-select: none;
    user-select: none;
  }
  img#logo {
    width: 128px;
    background-size: cover;
    border-radius: 200px;
    box-shadow: 0px 0px 40px rgba(63, 81, 181, 0.72);
    border: 3px solid #00a0ff;
    opacity: 1;
    margin: 0 auto;
    margin-top: 20px;
	margin-bottom: 20px;
	transition: all 1.0s;  
}
#logo:hover {
    box-shadow: 0 0 10px #fff;
    -webkit-box-shadow: 0 0 19px #fff;
    transform:rotate(360deg);
    -ms-transform:rotate(360deg); 	/* IE 9 */
    -moz-transform:rotate(360deg); 	/* Firefox */
    -webkit-transform:rotate(360deg); /* Safari 和 Chrome */
    -o-transform:rotate(360deg); 	/* Opera */
    filter:progid:DXImageTransform.Microsoft.BasicImage(rotation=3);
}
  h1 {
    font-family: 'Montserrat', 'Helvetica Neue', Arial, sans-serif;
    font-weight: 700;
    font-size: 30px;
    letter-spacing: 9px;
    text-transform: uppercase;
    margin: 12px 0;
    left: 4px;
  }
  h2 {
      color: #999;
      font-weight: normal;
      font-size: 15px;
      letter-spacing: .12em;
      margin-bottom: 30px;
      left: 3px;
  }
  p {
      font-size: 14px;
      line-height: 2em;
      margin: 0;
      letter-spacing: 2px;
  }
  h1, h2 {
    position: relative;
  }
  canvas {
    position: absolute;
    top: 0;
    left: 0;
    z-index: 0;
    width: 100%;
    height: 100%;
    pointer-events: none;
  }
  a {
    color: #999;
    text-decoration: none;
    transition: color .2s ease;
  }
  a:hover {
    color: #deba3b;
  }
  button {
    margin: 30px 20px;
    padding: 15px 20px;
    border-radius: 10px;
    border: 2px solid;
    font: 16px 'Open Sans', sans-serif;
    text-transform: uppercase;
    background: none;
    outline: none;
    cursor: pointer;
    -webkit-transition: all .5s;
    transition: all .5s;
    font-family:微软雅黑;
  }
  .btn {
  color: #A6ACEC;
  border-color: #A6ACEC;
  overflow: hidden;
  position: relative;
}
.btn:before, .btn:after {
  content: "";
  height: 100%;
  width: 0;
  position: absolute;
  z-index: -1;
  background-color: #A6ACEC;
  top: 0;
  -webkit-transition: all 0.25s;
  transition: all 0.25s;
}
.btn:before {
  left: 0;
}
.btn:after {
  right: 0;
}
.btn:hover {
  color: #27323A;
}
.btn:hover:before, .btn:hover:after {
  width: 50%;
}
</style>
