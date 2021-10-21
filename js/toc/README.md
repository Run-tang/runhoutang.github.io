# jekyll-table-of-contents

A simple JavaScript table of contents generator. Works well with [jekyll](https://github.com/mojombo/jekyll) static sites.

## Usage

### Basic Usage

The script requires jQuery. First, reference `toc.js` in templates where you would like to add the table of content.
Then, create an HTML element wherever you want your table of contents to appear:

```html
<div id="toc"></div>
```

Finally, call the `.toc()` function when the DOM is ready:

```html
<script type="text/javascript">
$(document).ready(function() {
    $('#toc').toc();
});
</script>
```

If you use redcarpet, you need to have the option `with_toc_data` in order to add HTML anchors to each header:
```yaml
markdown: redcarpet
redcarpet:
    extensions: [with_toc_data]
```

If you use rdiscount, enable the following option in order to generate the TOC:
```yaml
markdown: rdiscount
rdiscount:
    extensions:
      - generate_toc
```

### How It Works

The script works by looking for headers (h1, h2, h3, h4, h5, h6) which have an `id`.
An id is added automatically if you're using Jekyll and [Markdown](http://daringfireball.net/projects/markdown/syntax#header).

The table of contents automatically handles nesting of headers. For example, this Markdown post:

    ## Title
    ## Page 1
    ### Note on Paragraph 3
    ## Page 2
    ### Note on Paragraph 2
    ### Note on Paragraph 4

Will render this table of contents:

    1. Title
    2. Page 1
      a. Note on Paragraph 3
    3. Page 2
      a. Note on Paragraph 2
      b. Note on Paragraph 4
      
### Configuration

#### List Type
By default the table of contents is rendered as an `<ol>`, so you can change the number formatting using CSS.
However you can use the `<ul>` tag, using the `listType` option:

```javascript
$('#toc').toc({ listType: 'ul' });
```

#### Header Styling
The script also adds an `<i>` tag next to each header. This uses the class `icon-arrow-up`, which if you're using [Bootstrap](http://twitter.github.io/bootstrap/), will be an arrow pointing to the top of the page.
Clicking that arrow will scroll you to the top, while clicking on a header will get a permanent link to that particular header (using `window.location.hash`).

If you don't want this feature, add this setting:

```javascript
$('#toc').toc({ noBackToTopLinks: true });
```

Otherwise, you can use the stylesheet below to have the icon and the header aligned nicely:

```css
.clickable-header {
  cursor:pointer;
}
.clickable-header:hover {
  text-decoration:underline;
}
.top-level-header {
  display:inline;
}
.back-to-top {
  margin-left:5px;
  cursor:pointer;
}
```

#### Headers Used
By default the table of content is displayed when at least 3 headers are found. 
You can customize the minimum number of headers required with this setting:

```javascript
$('#toc').toc({ minimumHeaders: 2 });
```

And you can also select which headers you want to link to. By default `h1, h2, h3, h4, h5, h6` are displayed, but changing the `headers` setting lets you tweak it:

```javascript
$('#toc').toc({ headers: 'h3, h4, h5, h6' });
$('#toc').toc({ headers: '.content h1, .content h2, .content h3, .content h4, .content h5, .content h6' });
```

#### Effects
Finally, you can also change the way the toc is displayed, choosing a `slideShow` or a `fadeIn` effect instead of `show`:

```javascript
$('#toc').toc({ showEffect: 'slideDown' });
```

Otherwise, to deactivate the effect, set it up like this:

```javascript
$('#toc').toc({ showSpeed: 0 });
```

## Copyright

See LICENSE.txt for further details. But basically, do what you like with this.


一个简单的JavaScript内容表生成器。
与jekyll静态网站很好地工作。
该脚本需要使用jQuery。
首先，在你想要添加目录的模板中引用toc.js。
最后，当DOM准备好了，调用.toc()函数:}）;
</script>如果你使用redcarpet，你需要有选项with_toc_data，以便在每个头文件中添加HTML锚:这个脚本通过查找有id的头文件(h1, h2, h3, h4, h5, h6)来工作。
如果你使用Jekyll和Markdown，一个id会自动添加。目录自动处理标题的嵌套。
例如，这篇Markdown文章:## Title ## Page ## Note on Paragraph 3 ## Page ## Note on Paragraph 2 ### Note on Paragraph 4将呈现以下内容:标题2。a.第3段注释配置列表类型默认情况下，目录显示为<ol>，所以你可以使用CSS更改数字格式。
但是你可以使用<ul>标签，使用listType选项:$('#toc')。toc({listType: 'ul'});该脚本还在每个标题旁边添加了一个<i>标记。
这使用了类icon-arrow-up，如果你使用Bootstrap，它将是一个指向页面顶部的箭头。
点击箭头会滚动到顶部，而点击标题会得到一个到特定标题的永久链接(使用window.location.hash)。如果你不想要这个特性，添加如下设置:$('#toc')。toc({noBackToTopLinks: true});否则，你可以使用下面的样式表使图标和标题对齐得很好:} . click- header:hover {text-decoration:underline;} .top-level-header{显示:内联;} .back- top {margin-left:5px;光标:指针;默认情况下，至少找到3个header时显示内容表。
你可以用这个设置自定义所需的头文件的最小数量:$('#toc')。toc({minimumHeaders: 2});你也可以选择你想要链接的标题。
默认情况下，h1, h2, h3, h4, h5, h6显示，但改变标题设置让你调整它:$('#toc')。
Toc ({headers: 'h3, h4, h5, h6'});$ (" # toc”)。toc({头:”。内容h1， .内容h2， .内容h3， .内容h4， .内容h5， .内容h6'});
最后，你还可以改变toc的显示方式，选择slideShow或fadeIn effect而不是show: $('#toc')。
toc({showeeffect: 'slideDown'});否则，要禁用该效果，设置如下:$('#toc')。toc({showSpeed: 0});
更多细节请参见LICENSE.txt。但基本上，你喜欢怎么做就怎么做。
