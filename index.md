---
layout: home
---

<div class="index-content blog" id="main">
    <div class="section">
        <ul class="artical-cate" id="navigate">
            <li style="text-align:left" class="on"  id="link-blog"><a href="#blog"><span>Blog</span></a></li>
            <li style="text-align:center" id="link-opinion"><a href="#opinion"><span>Opinion</span></a></li>
            <li style="text-align:right" id="link-project"><a href="#project"><span>Project</span></a></li>
        </ul>

        <div class="cate-bar"><span id="cateBar"></span></div>

        <ul class="artical-list" id="blog">
        {% for post in site.categories.blog %}
            <li>
                <h2><a href="{{ post.url }}">{{ post.title }}</a></h2>
                <div class="title-desc">{{ post.description }}</div>
            </li>
        {% endfor %}
        </ul>
		
		<ul class="artical-list" id="opinion">
        {% for post in site.categories.opinion %}
            <li>
                <h2><a href="{{ post.url }}">{{ post.title }}</a></h2>
                <div class="title-desc">{{ post.description }}</div>
            </li>
        {% endfor %}
        </ul>
		
		<ul class="artical-list" id="project">
        {% for post in site.categories.project %}
            <li>
                <h2><a href="{{ post.url }}">{{ post.title }}</a></h2>
                <div class="title-desc">{{ post.description }}</div>
            </li>
        {% endfor %}
        </ul>	
    </div>
    <div class="aside" id="pic">
    </div>
</div>
 <script type="text/javascript">
    $("#link-blog").click(function(){
	    $("#main").attr("class","index-content blog");
	    $("#link-opinion").removeClass();
		$("#link-project").removeClass();
		$("#link-blog").addClass("On");
	});
	$("#link-opinion").click(function(){
	    $("#main").attr("class","index-content opinion");
	    $("#link-blog").removeClass();
		$("#link-project").removeClass();
		$("#link-opinion").addClass("On");
	});
	$("#link-project").click(function(){
	    $("#main").attr("class","index-content project");
	    $("#link-opinion").removeClass();
		$("#link-blog").removeClass();
		$("#link-project").addClass("On");
	});
</script>
