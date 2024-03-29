# Swipe functionality

- Install swipe package
- Import swipe functionality
```
  import { Swipe, SwipeItem } from "svelte-swipe";
```
- Create the swipe config constant with the name swipeConfig e.g.
```
const swipeConfig = {
    autoplay: false,
    delay: 2000,
    showIndicators: true,
    transitionDuration: 1000,
    defaultIndex: 0,
  };
```
- Specify swipe css attributes such as the dimensions of the swipe window e.g.
```
<style>
  .swipe-holder{
    height: 30vh;
    width: 100%;
  }
  img{
    max-width: 100%;
    height: auto;
  }
</style>
```
- Create a div for holding the swipe object and assign the created holder style to it
- Nest a Swipe component and send the config var as a prop
- In the Swipe component nest a SwipeItem for each image to be shown with a for each loop mayhaps e.g.
```
<div class="swipe-holder">
  <Swipe {...swipeConfig}>
    <SwipeItem>
      <img src="./images/1.jpg" alt="">
    </SwipeItem>

    <SwipeItem>
      <img src="./images/2.jpg" alt="">
    </SwipeItem>

    <SwipeItem>
      <img src="./images/3.jpg" alt="">
    </SwipeItem>

    <SwipeItem>
      <img src="./images/4.jpg" alt="">
    </SwipeItem>
  </Swipe>
</div>
```

## The other library

Boilerplate code goes here:
```
<script>

// Visit https://github.com/buhrmi/components for more Swipeable examples
import Swipeable from './Swipeable.svelte'

import {tick} from 'svelte'
let loginProgress, loginSwipeable, introProgress, zoomOut
tick().then(() => zoomOut = true)
</script>



<div id="wrapper">
  <div class="slides fullpage" style="transform: scale({1 - $loginProgress*0.3})">
		<Swipeable numScreens="3" let:current bind:progress={introProgress}>
		<section class:current={current == 0 && zoomOut}>
			<div class="topimage" style="opacity: {1 - Math.abs($introProgress)}">
				<div class="bg" style="background-image:url('https://images.unsplash.com/photo-1518335935020-cfd6580c1ab4?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=500&q=60')"></div>
				<div class="topgradient"></div>
				<div class="bottomgradient"></div>
			</div>
			<div class="content" style="right: {100 * $introProgress}%; opacity: {1 - Math.abs($introProgress)}">
				<h1>Your thumb.</h1>
				<h1>Incredible power.</h1>
				<p style="right: {150 * $introProgress}px">Discover the ultimate utilization of your thumb with <b>buhrmi's Svelte components</b> for touch-driven UIs. Swipe left to try.</p>
			</div>
		</section>
		<section class:current={current == 1}>
			<div class="topimage" style="opacity: {1 - Math.abs($introProgress - 1)}">
				<div class="bg" style="background-image:url('https://melissasiroisblog.files.wordpress.com/2015/04/tumblr_inline_moiixyhwbe1qz4rgp.jpg?w=620')"></div>
				<div class="topgradient"></div>
				<div class="bottomgradient"></div>
			</div>
			<div class="content" style="right: {100 * ($introProgress - 1)}%; opacity: {1 - Math.abs($introProgress - 1)}">
				<h1>Congratulations.</h1>
				<h1>You swiped.</h1>
				<p style="right: {150 * ($introProgress - 1)}px">You have experienced a smooth transition of content placed inside the <b>Swipeable</b> component. Cheers. But wait, there's more! Swipe again.</p>
			</div>
		</section>
		<section class:current={current == 2}>
			<div class="topimage" style="opacity: {1 - Math.abs($introProgress - 2)}">
				<div class="bg" style="background-image:url('https://images.unsplash.com/photo-1570030289513-f44af3cd0944?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=500&q=60')"></div>
				<div class="topgradient"></div>
				<div class="bottomgradient"></div>
			</div>
			<div class="content" style="right: {100 * ($introProgress - 2)}%; opacity: {1 - Math.abs(introProgress - 2)}">
				<h1>Change direction.</h1>
				<h1>Discover the vertical.</h1>
				<p style="right: {150 * ($introProgress - 2)}px"><b>Swipeable</b> also supports vertical swiping. Click "Sign In" to bring up vertically sliding content.</p>
			</div>
		</section>

		<div class="dots">
			<div class="dot active" style="left: {$introProgress * 14}px"></div>
			<div class="dot"></div><div class="dot"></div><div class="dot"></div>
		</div>

		<div class="btn" on:click={() => loginSwipeable.jump(1)}>Sign In</div>
			</Swipeable>
	</div>



	<div class="login fullpage" style="top: {100 * (1 - $loginProgress)}%">
		<Swipeable numScreens="2" direction="vertical" bind:this={loginSwipeable} bind:progress={loginProgress}>
		<div class="inner" style="top: {80*($loginProgress-1)}%">
			<div class="topimage">
				<div class="bg" style="background-image:url('https://steamuserimages-a.akamaihd.net/ugc/307738670230847301/02FCBC35FC39EC8A78464A4CB62F049987C44892/')"></div>
				<div class="topgradient"></div>
				<div class="bottomgradient"></div>
			</div>
			<p>
				This content slides vertically. Wowzers. Slide down to dismiss.
			</p>
			<h1>Sign In</h1>
			<div class="cancel" on:click|stopPropagation={() => loginSwipeable.jump(0)}>X</div>
			<input type="text" placeholder="E-mail address"><br>
			<input type="password" placeholder="Password"><br>
			<div class="btn">Sign in</div>
		</div>
			</Swipeable>
	</div>


</div>
<style>
.cancel {
	position: absolute;
	top: 3%;
	right: 6%;
	cursor: pointer;
}
.fullpage {
	position: absolute;
	width: 100%;
	height: 100%;
	overflow: hidden;
	user-select: none;
}
.fullpage .inner {
	width: 100%;
	height: 100%;
	position: absolute;
}
.login {
	background: black;
	text-align: center;
	top: 0;
}
.login .bg {
	transform: scale(1);
}
.login .inner {
	top: 0;
}

.btn {
	cursor: pointer;
	background: #927B62;
	color: white;
	padding: 10px 30px;
	display: inline-block;
}
.btn:hover {
	background: rgb(114, 96, 77);
}
.slides .btn {
	background: #927B62;
	color: white;
	position: absolute;
	bottom: 10%;
	left: 20px;
	right: 20px;
	padding: 12px 0;
	text-align: center;
}
section {
	position: absolute;
	width: 100%;
	height: 100%;
}
section p {
	position: relative;
}
h1 {
	position: relative;
}
.content {
	padding: 20px;
	position: relative;
}
.bg {
	background-position: center;
	background-size: cover;
	width: 100%;
	height: 100%;
	transform: scale(1.35);
	transition: all 9s ease-out;
}
.current .bg {
	transform: scale(1);
}
.topimage {
	width: 100%;
	height: 50%;
	overflow: hidden;
	position: relative;
}
.topimage .topgradient {
	background: linear-gradient(180deg, #000000AA, #00000000);
	position: absolute;
	top: 0;
	left: 0;
	width: 100%;
	height: 50%;
}
.topimage .bottomgradient {
	background: linear-gradient(0deg, #000000, #00000000);
	position: absolute;
	bottom: 0;
	left: 0;
	width: 100%;
	height: 30%;
}

.dots {
	position: absolute;
	bottom: 5%;
	left: 50%;
	transform: translateX(-50%);
	line-height: 0;
}
.dot {
	background: #444;
	width: 8px;
	height: 8px;
	margin: 0 3px;
	border-radius: 8px;
	display: inline-block;
}
.dot.active {
	position: absolute;
	background: #efefef;
}
#wrapper {
	position: absolute;
	top: 0;
	left: 0;
	height: 100vh;
	width: 100vw;
	overflow: hidden;
	margin: 0;
	font-family: Lato, -apple-system, BlinkMacSystemFont, Segoe UI, Oxygen, Ubuntu, Cantarell, Fira Sans, Droid Sans, Helvetica Neue, sans-serif;
	font-size: 15px;
	line-height: 1.5;
	color: #fafafa;
	background: black;
}
	h1 {
		margin: 0;
			line-height: 1.2;
	}

</style>
```