# Say Hello World

## The Code Editor
We’re finally ready to build our first Flask application. Well, it’s not going to be technically an application, but it will introduce us to some fundamental concepts, so that we’re ready to start building real applications.

At this point, if you are working with Mac or Windows, you’re going to need a code editor. If you use PythonAnywhere, don’t worry, you will be using their built-in code editor.

There are many good options for code editors. Some of the most popular include Sublime Text, PyCharm and Visual Studio Code. I definitely recommend to try out some of them when you have the time and see which one you feel most comfortable with.

However, for this course, I’ll be using Atom. Atom is really simple and powerful at the same time and I’ve been using it for some time, so I feel comfortable with it. 

So go ahead and install your code editor and we’ll start building our “Hello World” application next.

## Hello World

So let’s create a file inside our `simple_flask_app` folder. But first, we need to activate our virtual environments.

For Mac, open the terminal and `cd` to `/opt/simple_flask_app`. Then do `source venv/bin/activate` to activate virtualenv.

On Windows do `cd \opt\simple_flask_app`, then do `venv\Scripts\activate`

On PythonAnywhere do `cd ~/opt/simple_flask_app`, then do `workon simple_flask_app`.

From this point on, when I say “activate your virtualenv”, please follow the previous instructions for your current operating system.

Now we’ll create a new file called `hello.py` with our code editor inside the `simple_flask_app` folder.

For Windows and Mac type `atom .`. This will open the Atom editor with this folder selected. 

If you’re on a Mac and that command throws an error like “Atom was not found”, just make sure to quit the Atom application, open it again, and select “Install Shell Commands”.

![](images/3.2.1.png)

So how do we create `hello.py`?

On Windows and Mac, select the `simple_flask_app` folder first with your mouse and then hit the `a` key. On the input field type `hello.py`. Note that your folder might have "contracted". Just click it again to expand it and see the contents.

On PythonAnywhere hit the "hamburger" icon on the top right, and select "Files".

![PythonAnywhere Files](images/3.2.2.png)

Then locate the `opt/` folder on the Directories section, click on it and then click on the `simple_flask_app` link. Make sure you have the full path `/home/` your username, `/opt/simple_flask_app` on the top left.

![The right directory](images/3.2.3.png)

Finally on the “Files” section, enter “hello.py” and click on the “New file” button.

![New file](images/3.2.4.png)

Okay, we’re ready to start coding our first Flask application!

On the first line type:

{lang=python,line-numbers=on,starting-line-number=1}
```
from flask import Flask
```

This imports the Flask class in our file.

We now need to create an instance of the class. We’ll call that object “app”:

{lang=python,line-numbers=on,starting-line-number=2}
```
app = Flask(__name__)
```

Notice we pass `__name__` as a parameter. This is a Python built-in magic variable that tells Flask which module or package this is running from. This allows Flask to know where to look for related folders of our application.

Leave an empty line and now type:

{lang=python,line-numbers=on,starting-line-number=4}
```
@app.route('/')
```

The @ sign here is called a “decorator”, and essentially this allows us to modify the function we’ll type underneath. We’ll learn more about decorators later on.

The “route” decorator tells Flask what URL this function will be called on. In this case this will be the root folder or “/“.

We now create our function, which just returns “Hello World” back to the browser:

{lang=python,line-numbers=on,starting-line-number=5}
```
def hello_world():
    return 'Hello, World!'
```

And that’s it! This is what the whole file looks like:

![Hello World!](images/3.2.5.png)

In the Atom editor, notice how there’s a little blue circle on the tab? That means this file hasn’t been saved. Hit “CTRL+s” on Windows or “Command+s” on Mac to [save it](https://github.com/fromzeroedu/itfc-simple-flask-app/blob/step-1/hello.py).

On Python Anywhere, notice how it says “unsaved changes” on the top next to the file’s path. Hit the green “Save” button to save the file.

Now we’ll see how to run this application and see it in our browser. We have two different lessons depending if you’re in Windows or Mac, or if you’re in PythonAnywhere. Skip to the one that’s right for you.

## Running the Application (Windows and Mac)

Let’s see how we run the application on Windows or Mac.

Once again, make sure to have your virtualenv activated, so that the word `(venv)` appears on the command prompt. If it doesn’t, activate it.

To be able to run the application, we first need to set an environment variable to tell Flask what application we want to run and then use the `flask run` command.

In Windows Powershell, set the environment variable with the following command:

{lang=bash,line-numbers=off}
```
$env:FLASK_APP = "hello.py"
```

In Mac OS, you set it by doing:

{lang=bash,line-numbers=off}
```
export FLASK_APP=hello
```

We can now run the application by typing the following command:

{lang=bash,line-numbers=off}
```
flask run
```

Now open your browser and type this URL: `http://127.0.0.1:5000/`

That `127.0.0.1` is also called localhost and it’s a special IP address that points back to your own machine.

You should now see the string “Hello, World!” appear in your browser.

![Hello there!](images/3.3.1.png)

That’s it, our first Flask application!

Stop the application by going back to the terminal and hitting “CTRL-C” on the running task.

Keep in mind that the `FLASK_APP`environment variable will be erased when you close your terminal, so if you stop here or restart your terminal or computer, you need to set the environment variable again. We will see how we can do this automatically later in the course.

## Running the Application (PythonAnywhere)

To run our application on PythonAnywhere, we need to register a web app on their system.

So from the navigation menu click on “Web” and you will land on this screen.

![Web app screen](images/3.4.1.png)

Click on the “Add a new web app” button. You will be notified of the URL that has been assigned to you. Usually this is your username, dot, pythonanywhere dot com. For free accounts that’s the only option. Paid accounts can use custom URLs. Click “Next”.

![App domain name](images/3.4.2.png)

In the next screen you select a Python Web framework. Since we installed Flask ourselves via our virtualenv, select “Manual configuration".

![Manual configuration](images/3.4.3.png)

The next screen asks what Python version to use. Select “Python 3.6” and click “Next”.

![Python selection](images/3.4.4.png)

The next screen talks about the creation of a WSGI configuration file. Don’t worry too much about what WSGI means now, just think of it as a file that tells the PythonAnyhwere server which application should be associated with your URL. PythonAnywhere will create a default WSGI file for you to edit on the next screen. Click “Next”.

![WSGI information](images/3.4.5.png)

Now we’re into the “Configuration” page. There are some things to do here.

First, notice the “Best before date” section. If you have a free plan, that means that at least once every three months you need to press that yellow button that reads “Run until 3 months from today”. PythonAnyhwere does this to make sure users that are using the servers are actively doing so.

![Best before date](images/3.4.6.png)

Next, on the “Code” section you need to select the “Source code” directory. Click on the blue link and enter the following path, replacing the `username` with your own username:

{lang=bash,line-numbers=off}
```
/home/your_username/opt/simple_flask_app
```

Next on the “WSGI configuration file” you’ll need to replace the file contents with the following code. Just click on the blue link and enter this snippet, replacing the _username_ with your own username. [Save the file](https://github.com/fromzeroedu/itfc-simple-flask-app/blob/step-1/pa_wsgi.py).

{lang=python,line-numbers=on,starting-line-number=1}
```
import sys
python_anywhere_username = 'jorge3'
path = '/home/' + python_anywhere_username + '/opt/simple_flask_app'
if path not in sys.path:
    sys.path.append(path)

from hello import app
app.debug = False

from werkzeug.debug import DebuggedApplication
application = DebuggedApplication(app, evalex=True)
```

We’re almost done. Now head over to the “Virtualenv” section and select the blue link and just type “simple\_flask\_app”. PythonAnywhere will auto-complete with the full path when you hit enter.

So the whole thing should look like this, but with your own username.

![The whole PythonAnywhere setup](images/3.4.7.png)

Finally, go to the top of the page and click on the green button on the “Reload” section.

![Reload button](images/3.4.8.png)

Now click on the blue URL on the top or enter “yourusername.pythonanywhere.com” in the browser. You should see the “Hello, World!” text.

![PythonAnyhwere Hello World](images/3.4.9.png)

If something didn’t work, just re-check the steps and make sure you’re not missing something. It’s usually some silly small detail you missed.
