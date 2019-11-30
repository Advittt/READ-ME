## PYTHON:
from flask import Flask, render_template, request
app = Flask(__name__)

@app.route('/')
def contact():
   return render_template('contact.html')

from flask import redirect
@app.route('/goToBedfordSchool')
def goToBedfordSchool():
    return redirect('https://www.bedfordschool.org.uk/')

from flask import Request
@app.route('/getRadius', methods = ['POST', 'GET'])
def getRadius():
    if request.method == 'GET':
        radius = request.args.get('radius')
        radius = int(radius)
        return render_template("circles.html",radius=radius)       



if __name__ == '__main__':
   app.run(debug = True)

## TEMPLATES:
## conatact.html:

<!DOCTYPE html>
<html>
<body>
<h2 style="color:blue">Redirecting Button</h2>
<p>When clicking this form(button), you will be redirected to Bedford School website:</p>

<form action="/goToBedfordSchool" target="_blank">
    <input type="submit" name="submit_button" value="Go To Bedford School">
</form> 

<form action="/getRadius">
    input radius:
    <p><input type="number" name="radius" min="1" max="10"/></p>
    <p><input type = "submit" value = "submit" /></p>
</form>
         
</body>
</html>

## circles.html:

<!DOCTYPE html>
<html>
   <body>
    <h1>Radius= {{ radius }}</h1>
    

   </body>
</html>
