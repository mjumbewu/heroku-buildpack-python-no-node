Heroku buildpack: GeoDjango
========================

This is a [Heroku buildpack](http://devcenter.heroku.com/articles/buildpacks) for GeoDjango apps.
It extends the original Python buildpack by adding GEOS, Proj.4 and GDAL, per the [GeoDjango installation
instructions](https://docs.djangoproject.com/en/dev/ref/contrib/gis/install/).

This buildpack assumes your PostGIS server lives outside the Heroku stack, though we'd love to see it
forked to handle any setup for Heroku's Postgres services.

Usage
-----

Example usage:

    $ heroku create --stack cedar --buildpack https://github.com/cirlabs/heroku-buildpack-geodjango/

    $ git push heroku master
    ...
    -----> Heroku receiving push
    -----> Fetching custom buildpack... done
    -----> Python app detected
    -----> Fetching and installing GEOS 3.3.2
    -----> Installing ...
       GEOS installed
    -----> Fetching and installing Proj.4 4.7.0
    -----> Installing ...
       Proj.4 installed
    -----> Fetching and installing GDAL 1.8.1
    -----> Installing ...
       GDAL installed
    -----> Preparing virtualenv version 1.7
    ... etc.

Notes
-----

All libraries are stored in /app/.github.

IMPORTANT: You will need to set two Django settings in order for GEOS and GDAL to work properly!

GEOS_LIBRARY_PATH = '/app/.geodjango/geos/lib/libgeos_c.so'

GDAL_LIBRARY_PATH = '/app/.geodjango/gdal/lib/libgdal.so'