## SOF Week - API & Data Integration

This web app simulates data feed and api integrations on a map of Raleigh, NC. The user can click on a map marker for each park and view or upload pictures taken at that park. Location data is pulled from one of the [Open Data Raleigh APIs](http://data-ral.opendata.arcgis.com/). Then, it uses [React-Leaflet](https://react-leaflet.js.org/) to handle the map features. Finally, it’s using [Cloudinary](https://cloudinary.com/) to host the images that are uploaded.

## Setup and Dependencies

To deploy this app, you'll need a Cloudinary account -- the free tier is fine -- an OpenShift account, and the oc command line tool. If you don't have one, you can create an OpenShift account [here](https://manage.openshift.com/sign_in).

## Deploying SOF-Week-App to OpenShift

    oc login <...>
    oc new-project sof-week
    oc new-app https://github.com/mainsail44/sof-week-2023.git \
       -e CLOUDINARY_NAME=<your-cloudinary-name> \
       -e CLOUDINARY_KEY=<your-cloudinary-key> \ 
       -e CLOUDINARY_SECRET=<your-cloudinary-secret>
    oc logs -f bc/sof-week-2023
    oc expose service sof-week-2023
    oc get route
