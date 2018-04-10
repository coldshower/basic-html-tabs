# basic-html-tabs
barebones tabs with just html, css, and vanilla js

html
```html
<!DOCTYPE html>
<html>
<head>
	<title>Basic Html Tabs</title>
	<link rel="stylesheet" href="styles.css">
</head>
<body>
	<div class="tab-header">
	  <ul>
	    <li class="selected-tab">first</li>
	    <li>second</li>
	    <li>third</li>
	  </ul>
	</div>
	<div class="tab-content selected-tab-content">
	  first
	</div>
	<div class="tab-content">
	  second
	</div>
	<div class="tab-content">
	  third
	</div>
	<script src="main.js" type="text/javascript"></script>
</body>
</html>
```

javascript
```js
var tabs = document.getElementsByClassName('tab-header')[0].children[0].children;

var tabContents = document.getElementsByClassName('tab-content');

var tabLength = tabs.length;

for (var i = 0; i < tabLength; i++) {
  (function (index) {
    tabs[index].addEventListener('click', function (e) {
      selectTab(index);
      selectTabContent(index);
    });
  })(i);
}

function selectTab(selectedIndex) {
  for (let i = 0; i < tabLength; i++) {
    if (selectedIndex === i) {
      tabs[i].className = 'selected-tab';
    } else {
      tabs[i].className = '';
    }
  }
}

function selectTabContent(selectedIndex) {
  for (let i = 0; i < tabLength; i++) {
    if (selectedIndex === i) {
      tabContents[i].className = 'tab-content selected-tab-content';
    } else {
      tabContents[i].className = 'tab-content';
    }
  }
}
```

css
```css
.tab-header ul {
	list-style: none;
	margin: 0;
	padding: 0;
	display: flex;
	justify-content: space-between;
}

.tab-header ul li {
	box-sizing: border-box;
	flex-grow: 1;
	padding: 15px;
	text-align: center;
	border-radius: 5px 5px 0 0;
	border-bottom: 1px solid grey;
}

.tab-header ul li.selected-tab {
	border-left: 1px solid grey;
	border-right: 1px solid grey;
	border-top: 1px solid grey;
	border-bottom: 0;
}

.tab-content {
	padding: 15px;
	display: none;
}

.selected-tab-content {
	display: block;
}
```
