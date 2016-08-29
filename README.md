# Bluemix_NLC_Nodejs
Use natural language classifier API on Bluemix by Node.js

[![Node.js 4.4.5](https://img.shields.io/badge/Node.js-4.4.5-orange.svg)](https://nodejs.org/en/)
[![Platforms OS X | Windows | Linux |](https://img.shields.io/badge/Platforms-OS%20X%20%7C%20Windows%20%7C%20Linux%20-lightgray.svg)](https://nodejs.org/en/)

# What is this repository for? ###

* Quick summary: Use natural language classifier API on Bluemix by Node.js
* Version 1.1.0

# How do I get set up? ###

Documentation: Read [IBM Watson Developer Cloud](https://www.ibm.com/watson/developercloud/doc/nl-classifier/) to know concept and flow. Sign up/in on [Bluemix](ng.bluemix.net) and crate a natural language classifier service with `usr/pwd`.

# Preparation ###

1. Apply a Bluemix account.
2. Be familiar with Nodejs fundamentation.

# Stage One - Set up service ###

1. Log in at [Bluemix](http://ng.bluemix.net) website.
2. Go to catalog and find the NLC service.
![Catalog](/screenshots/Catalog.png)
3. Type a unique name for the service instance in the Service name field. Leave the default values for the other options.
4. In your Service Credentials, bear in mind your *username* and *password*. 
![Catalog](/screenshots/Credentials.png)

# Stage Two - Create and train a classifier ###

1. Go to Nodejs SDK from [Github](https://github.com/watson-developer-cloud/node-sdk) page which is developed by IBM.
2. Install node-nodule: 
```
$ npm install watson-developer-cloud --save
```
3. Go to **examples** and deep into the codes for *natural_language_classifier.v1.js*.
4. Replace *username* and *password* Service Credentials on the previous stage.
5. There is a bug in code please fix it first. (lost extension for csv) 
6. Create a classier for corresponding file **just one time**.
```javascript
// Create Classifier
natural_language_classifier.create(params, function(err, response) {
  if (err)
    console.log(err);
  else
    // copy the classifier_id from the response
    console.log(JSON.stringify(response, null, 2));
});
```
```
$ node NLC.js
```
7. See the result, keep the **classifier_id** and comment classifier for the **create** function.
8. You can see the status is “Training.” So you should wait for a few minutes.
9.  Enter the **classifier_id** for using a classifier.
```javascript
// Using a Classifier
natural_language_classifier.classify({
  text: '<question>',
  classifier_id: '<classifier_id>' }, // from the previous command
  function(err, response) {
    if (err)
      console.log('error:', err);
    else
      console.log(JSON.stringify(response, null, 2));
});
```
# Host a server to test ###
0. ```cd to/path```
1. Install modeules: 
    ```$ npm install``` (if you encouter permission problems: sudo npm install)
2. use your classifier_id in Web app or NLC.js.
3. run the project: 
    ```node index.js```
4. Open **127.0.0.1:3000** on your browser.
5. You will see Sample page.
6. Enjoy it (Ask something).
7. Remember Close the sever by Ctl+c

# How to run program ###
* Use CMD/Terminal
* Web browser

# Contribution guidelines ###
* [IBM Watson Developer Cloud](https://www.ibm.com/watson/developercloud/doc/nl-classifier/)
* Bo Cheng Huang
