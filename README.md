# Putting it All Together: Client-Server Communication

## Learning Goals

- Understand how to communicate between client and server using fetch, and how
  the server will process the request based on the URL, HTTP verb, and request
  body
- Debug common problems that occur as part of the request-response cycle

## Introduction

Just like the last lesson, we've got code for a React frontend and Rails API
backend set up. This time though, it's up to you to use your debugging skills to
find and fix the errors!

To get the backend set up, run:

```console
$ bundle install
$ rails db:migrate db:seed
$ rails s
```

Then, in a new terminal, run the frontend:

```console
$ npm install --prefix client
$ npm start --prefix client
```

Confirm both applications are up and running by visiting
[`localhost:4000`](http://localhost:4000) and viewing the list of toys in your
React application.

## Deliverables

In this application, we have the following features:

- Display a list of all the toys
- Add a new toy when the toy form is submitted
- Update the number of likes for a toy
- Donate a toy to Goodwill (and delete it from our database)

The code is in place for all these features on our frontend, but there are some
problems with our API! We're able to display all the toys, but the other three
features are broken.

Use your debugging tools to find and fix these issues.

There are no tests for this lesson, so you'll need to do your debugging in the
browser and using the Rails server logs and `byebug`.

**Note**: You shouldn't need to modify any of the React code to get the
application working. You should only need to change the code for the Rails API.

As you work on debugging these issues, use the space in this README file to take
notes about your debugging process. Being a strong debugger is all about
developing a process, and it's helpful to document your steps as part of
developing your own process.

## Your Notes Here

- Add a new toy when the toy form is submitted

  - How I debugged: First we tested out the "add toy" button in the browser. Once we input our own information, we got an error in the terminal that said: "NameError (uninitialized constant ToysController::Toys):"... This error prompted us to check our toy_controller. Once there, we saw that the Toy model was misspelled as "Toys" in the create method. 

- Update the number of likes for a toy

  - How we debugged: Kyle and I debugged this issue by first opening up the in browser console... We saw that there was an error that gave us a prompt which stated there was an error with the JSON input. Kyle had then pointed out that we should look at the controller file to make sure that all of the resources were correct and we were calling the correct methods on the actions we wanted performed. Once inside the toys controller file, we saw that the update action/method was missing a render json: toy.

- Donate a toy to Goodwill (and delete it from our database)

  - How I debugged: First I tested out the "donate to goodwill" button on the website... In my terminal, after initiating the donate action, I received a prompt that said "ActionController::RoutingError (No route matches [DELETE] "/toys/1"):"... This lead me to believe that we were missing something in the routes file. I then checked the routes file out, and saw that there wasn't a :delete symbol, so  just ended up deleting the existing information and only left in toys. This then allowed the website to work as intended. 
