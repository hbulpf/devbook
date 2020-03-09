# flask 问题


## 1. Flask中 template中的html，如何引用static中的css，js?

```
<link rel="stylesheet" href="{{ url_for(‘static’, filename=’css/framework7.ios.css’) }}">
<img src="{{ url_for(‘static’, filename=’img/avatar/navi_add_lightblue_24x24.svg’) }}"/>
```

参考: https://www.crifan.com/flask_html_template_how_reference_css_js_assets/