
## Part 0 (B): Preparation: deploy to Heroku
- Log in to heroku with `heroku login` or (`heroku login -i` for terminal-based login).
- Create a new app on Heroku with `heroku create`
- Heroku will assign your app a whimsical name such as `luminous-coconut-237`; once your app is deployed, you would access it at `http://luminous-coconut-237.herokuapp.com`.  Finally, we deploy our app to Heroku:

```sh
$ git push heroku master
```
Is the app running on Heroku?  If you navigate to the heroku URL that is printed at the end of the results from `git push heroku master` you'll get a "We're sorry, but something went wrong." error in the browser.  

We can get a hint as to why by running the following command:

```sh
$ heroku logs
```

which will show an error like:

```
ActionView::Template::Error (PG::UndefinedTable: ERROR:  relation "movies" does not exist
```

Just as we ran `rake db:migrate` and `rake db:seed` to do first-time database creation locally, we must also cause a database to be created on the Heroku side:

```sh
$ heroku run rake db:migrate
```

and

```sh
$ heroku run rake db:seed
```

Now you should be able to navigate to your app's URL.  `heroku open` opens your browser to that URL in case you forgot it, however this command does not work on c9, where you will need to navigate to the relevant URL.

**Note:** don't proceed past this point until you are able to complete the above successfully, or you won't be able to receive a grade for this assignment!

Next: [Part 1: Sort the list of movies](part_1.md)
