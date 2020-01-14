```python
from flask import Flask, render_template, request
app = Flask(__name__)

@app.route('/')
def contact():
   return render_template('getDog.html')

from flask import redirect
@app.route('/getDog')
def getDog():
    import json
    from urllib.request import urlopen
    with urlopen('https://dog.ceo/api/breeds/image/random') as response:
        source = response.read()
    data = json.loads(source)
    https = data['message']
    return redirect(https)

if __name__ == '__main__':
   app.run(debug = True)

```
Templates:
getDog:
```html
<!DOCTYPE html>
<html>
<body>
<h2 style="color:blue">Random Dog Generator</h2>
<form action="/getDog" target="_blank">
    <input type="submit" name="submit_button" value="find a dog">
</form> 

</body>
</html>
```

