# BLOG DJANGO NOTES
# Heroku Deployment
- heroku login
- heroku create $name
- heroku git:remote -a $name
- pipenv install whitenoise
## SETTINGS FILE
- Add 'whitenoise.runserver_nostatic' in INSTALLED_APPS (must be above the built in static files)
- Add 'whitenoise.middleware.WhiteNoiseMiddleware' in MIDDLEWARE (on the third line)
  ## At the bottom add
  - STATIC_ROOT = BASE_DIR / 'staticfiles'
  - STATICFILES_DIRS = [BASE_DIR / 'blog/static']
  - STATIC_URL = 'static/'
  - STATICFILES_STORAGE = 'whitenoise.storage.CompressedManifestStaticFilesStorage'

- Commit to Github
  ### Push it to heroku as below:
  - git push heroku master
  - heroku ps:scale web=1
- Heroku open (opens the app)
