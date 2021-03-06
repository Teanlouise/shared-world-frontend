[Back to Home](https://teanlouise.github.io)

![sw_frontend](sw_frontend_title.PNG)

[Overview](https://teanlouise.github.io/shared-world)     |     [Develop](https://teanlouise.github.io/shared-world/develop)    |  [Deploy](https://teanlouise.github.io/shared-world/deploy)    |   [Data](https://teanlouise.github.io/shared-world-data)

This is the frontend implementation of the shared-world application. Connection with the Django backend is through axios to access rest API functionality. This application is deployed on Firebase with access to App Engine, Cloud Storage and GoogleMapsAPI.

This is the first project I have built using React. Followed a [JustDjango Youtube tutorial](https://www.youtube.com/watch?v=uZgRbnIsgrA) to assist with the process.

I used [AntDesigns](https://ant.design/) templates for quicker development and clear layout and [VisualStudio](https://automationpanda.com/2018/02/08/django-projects-in-visual-studio-code/) for coding.

# Setup
These are the steps I went through to start the project

### Create React Project
- [Install node.js](https://www.guru99.com/download-install-node-js.html#1) – no customised settings
- Open “Windows Powershell”
- Go to project directory
```
cd shared.world
```
- Make directory for frontend
mkdir frontend
- No virtual environment
- Start frontend project
```
npx create-react-app gui
```
- Go into project folder
cd gui
- Runproject
```
npm start
```
- Check running
- Remove import logo 
- Add containers folder under src
- Add components folder under src

### Installations:

- Use antd templates
```
npm install antd
```
- Use axios to connect to backend via API
```
npm install axios
```
- Use router-dom for easier page connections
```
npm install --save react-router-dom
```

### Layout
- Go to App.js
- remove everything
- Import antd
```
import 'antd/dist/antd.css'
```

### Containers
- Layout.js
- HomeView.js 
- AboutView.js 
- PostList.js
- Post Detail.js
- ProfileList.js

### Components
- Posts.js
- Profiles.js

# PAGES

### Login
- Default page
- Choose to login or register
- When login redirected to home
- Uses token authentication with redux
- Once logged in there is a button to logout
- Logout and register redirects to login page

### Home
- Main page for the application
- Dropdown menu of all pre-defined countries
- [Google GeoChart map](https://developers.google.com/chart/interactive/docs/gallery/geochart) with countries coloured according to their tourist-to-local ratio (data from queries on the WorldBank public dataset in BigQuery, find at 2017_ratio in [shared-world-data](teanlouise.github.io/shared-world-data) repo)
- When users select submit they are redirected to a PostList page

### About
- static page explaining how the app works
- initial first step of selecting continent not implemented

### Profile
- List of all profiles of users in database
- Todo: Show the ProfileDetail view of the current user (not implemented due to complexity of authentication)

### PostList
- Posts are ordered according to the users interests, with the most matches first (generated by Spark program, find at post_match in shared-world-data repo)
- The data is retrieved from JSON files stored for each user according to country on GCS
- When the title of the post is selected, redirected to PostDetail View

### PostDetail
- Shows the details of the seleced post on the left and a card of the author's details on the left
- Selecting the username of the author will take to ProfileDetail

### ProfileDetail
- Shows the details of the selected profile in a card on the left and all the posts written by them on the right
