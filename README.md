

[![Deploy](https://www.herokucdn.com/deploy/button.svg)](https://heroku.com/deploy?template=https://github.com/Itxxwasi/DWATSON-DB.git)

Option B (CLI):

```powershell
heroku login
heroku create your-app-name
heroku git:remote -a your-app-name
git push heroku main
heroku config:set MONGODB_URI="your_production_mongo_uri"
heroku ps:scale web=1
heroku open
```

Notes:
- The server listens on the port provided by Heroku via the `PORT` environment variable.
- You must set `MONGODB_URI` (or `MONGO_URL`) in Heroku config vars to point to your MongoDB Atlas cluster.
- The `Procfile` in the repo already points Heroku to start `node server/index.js`.

