Let's take a quick break from the main Express tutorial to practice what we've already learned.  At this point you should know enough to use Express to make some fun interactive web apps! We're going to create a super simple message board.

SHOULD PROBABLY HAVE SOME NEWB GO THROUGH THIS TO MAKE SURE I DIDN'T MISS ANYTHING IMPORTANT LOL

### Assignment

<div class="lesson-content__panel" markdown="1">

1. Use `express-generator` to set up a basic project using whichever templating language you prefer.  Examples here will use `ejs`, but feel free to use Pug if you enjoy it. The generator will give you more than you really need at this point, but don't worry about it too much we're just going to ignore everything that we aren't using.  If you prefer you can set it all up manually -- it doesn't really take that much longer.
2. We are going to have 2 routes, the index (`"/"`) and a new-message form (`"/new"`). The generator already created a router for our index so find that file and open it up.  It can be found at `routes/index.js`. There is already an app.get for `"/"` that should be rendering your index view, so create the app.get() for `"/new"` and point it to a new view called `"form"`.
3. In the views directory create your `form` template. Add a heading and give it 2 inputs (one for the author's name and one for the message text) and a submit button. To make the form actually  make a network request you will need to define it with both a method and an action like so:

~~~html
<form method="POST" action="/new">
  put your inputs and buttons in here!
</form>
~~~

4. With your form set up like this, when you click on the submit button it should sent a POST request to the url specified by the action attribute, so go back to your index router and add an `app.post()` for `"/new"`.
5. To actually get and use the data from your form we need to install a middleware function called `body-parser`. Install it with `npm install body-parser` and then add the following code to your app.js to use it.  Once this code is added you should be able to access the contents of your form inside `app.post()` as an object called `req.body`. The individual fields inside the body object are named according to the `name` attribute on your inputs (`<input name="message-text">` etc.).

~~~javascript
// near the top of your file:
const bodyParser = require('body-parser');

// near the rest of your middleware, but before the index route is defined:
app.use(bodyParser.urlencoded({ extended: false }));
~~~
6. In your index router file create an array called `messages` and then in you `app.post()` take the contents of your form submission and push them into that array as an object that looks something like this:
~~~javascript
messages.push({text: messageText, user: messageUser, added: new Date()})
~~~
at the end of the `app.post()` function use `res.redirect('/')` to send users back to the index page after submitting a new message.
7. All that's left, then is to display your messages on your index page! Using whatever templating language you selected in your index template, loop through the array of messages and display the user, text, and date for each one.
8.  At this point, you should be able to visit `/new` (it might be a good idea to add a link to that route on your index page), fill out the form, submit it and then see it show up on the index page!
9. ADD INSTRUCTIONS FOR DEPLOYMENT
</div>

### Student Solutions
To add your solution to the list below, edit this [file](#) (located on The Odin Project's "curriculum" github repository). See the section on [Contributing](http://github.com/TheOdinProject/curriculum/blob/master/contributing.md) for more instructions.

<details markdown="block">
  <summary> Show Student Solutions </summary>

- Add your solution below this line!

</details>
