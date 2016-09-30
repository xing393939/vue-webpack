<template>
<div id="nav">
	<div class="wrapper">
		<div id="logo"><a href="/"><img src="/static/logo.png" /></a></h1></div>
		<ul>
			<li id="category-all"><a href="/">全部</a></li>
			<li id="category-tech"><a href="/category-tech.html">技术</a></li>
			<li id="category-essay"><a href="/category-essay.html">随笔</a></li>
			<li id="category-reading"><a href="/category-reading.html">阅读</a></li>
			<li id="category-quotes"><a href="/quotes.html">引言</a></li>
		</ul>
	</div>
</div>
<div class="wrapper main">
    <div id="content" class="index">
        <!-- main view -->
        <router-view
          class="view"
          keep-alive
          transition
          transition-mode="out-in">
        </router-view>
    </div>
    <div id="footer">
    	<p style="color:#ccc;font-size:12px;text-align: center">make the world a little better and easier</p>
    	<p style="clear:both"></p>
    </div>
</div>
</template>

<style>
    @import '../css/style.css';
    @import '../css/syntax.css';
</style>
