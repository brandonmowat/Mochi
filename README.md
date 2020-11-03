![Mochi Logo]()

# Mochi 🍬
Mochi is a simple, open source, blogging platform for you to share your thoughts and ideas. The main differentiator between Mochi and other vanilla blogging platforms is that it has an iOS companion app for writing your content on.

[Mochi iOS Editor](https://github.com/brandonmowat/Mochi-iOS) |
[Mochi API](https://github.com/brandonmowat/Mochi-API) |
[Mochi Web](https://github.com/brandonmowat/Mochi-Web)

## Motivation

The reason I built Mochi is because I felt the blogging tools available to me were lacking this sort of "in between" where I could easily spin up a full-featured blog, have an iOS native writing experience, and still have full control over how it's deployed and the code.

## Who is Mochi for?

Mochi has been built for a more technical user. It requires a fair amount of technical knowledge to set up — if you're browsing GitHub and have some familiarity with the command line, then you'll be able to set up your own blog on with Mochi.

## How does Mochi work?

![Mochi Architecture](https://i.imgur.com/GOZM9pn.png)

## How do I set it up?

You can deploy Mochi however you like, but in these instructions, I'll be walking you through the same setup as I use and is illustrated in the above diagram.

1. Set up API [Mochi API](https://github.com/brandonmowat/Mochi-API)
2. Set up your database
3. Download the iOS App [Mochi iOS Editor](https://github.com/brandonmowat/Mochi-iOS)
4. Set up web view [Mochi Web](https://github.com/brandonmowat/Mochi-Web)


### Set up the API

You'll want to create a Heroku account if you don't have one already. Clone the Mochi API and push it to your new heroku server.

#### Environment Variables

You'll need to set the following environment variables:
- `MONGODB_URI` (You'll create this in the next step)
- `BUILD_HOOK_URL` (Your netlify build hook)
- `ADMIN_USERNAME` (you'll need these for API Authentication)
- `ADMIN_PASSWORD`

### Set up your Database

Out of the box, Mochi only supports MongoDB as the datastore. I recommend either MongoAtlas or mLab.

Once created, get your mogodbURI. Add `MONGODB_URI` as an environment variable wherever you're going to be deploying to (I use Heroku).

### Download the iOS App

You can do this by cloning the App and running it on your phone or iPad. There aren't any articles yet because mochi doesn't know where your server is or have the credentials to connect. To set it up, open the settings modal by hitting the Settings button in the top left of the app. Input the api path (it's your `heroku url` + `/api/v1/`), as well as the admin username and password.

### Deploy your web view

I built Mochi with Netlify in mind and I recommend using them for your own instance. I'll assume you're going to use them as well 😊

Make sure to also set the `API_ROOT` environment variable in the `.env`. 
For my own blog, that's `https://brandon-server.herokuapp.com/articles/`

Clone/Fork Mochi Web and push it to your own git repo. Create a Netlify account -- it's free. Go into Netlify and _Create a new site from git_. Once that's live, create a new Build Hook from your website settings in Netlify. Grab that URL and add it as an environment variable called `BUILD_HOOK_URL` in your API (in Heroku).

### TADA 🎉

You did it! Everything should work as expected. You should now be able to write new articles on the iOS app and have them build as static files to your blog.

If you have any bugs, tweet at me or create an issue.

Thanks for using Mochi 🎉

## TODO:

- [x]  Create SSR Web blog
- [x]  Create API to manage article content
    - [x]  Create articles
    - [x]  Fetch articles
    - [x]  Patch articles
    - [x]  Delete articles
- [x]  Create iOS app to write new, update, and delete content
- [x]  Add Markdown support
- [ ]  Add a web editing version
- [x]  Add API validation
- [ ]  Add API Docs
- [ ]  Add users collection for contributing users
- [x]  make content view not autofocus (iOS)
- [x]  Add shortcut to save (iOS)
- [ ]  Versioning?
- [ ]  Put App on the App Store
