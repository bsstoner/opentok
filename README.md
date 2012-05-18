# OpenTokSDK for node.js

  node.js version of OpenTok's Server Side SDK, ported from their
Python/Ruby versions.

## Install

    npm install opentok

## Example

    var opentok = require('opentok')
      , globalSession;

    // creating an instance of the SDK:

    var ot = new opentok.OpenTokSDK('apikey','apisecret')

    // creating a video chat session for everyone:

    ot.createSession('localhost',{},function(session){
      globalSession = session
    })

    // Then on page load, generate a token for each user, and 
    // use your sessionId and token in the client side js to load the 
    // video session from tokbox.  See their extensive client side examples at http://tokbox.com

    ot.generateToken({sessionId:globalSession.sessionId})

    // you can pass other tokbox params to generateToken, like what role that user should have (default is PUBLISHER):

    ot.generateToken({
      session: globalSession,
      role: "moderator",
      connection_data: "userid_" + new Date().getTime()
    });


  There is a basic working example in examples/app.js


## Questions?

  OpenTok Docs:
  http://www.tokbox.com/opentok/tools/js/gettingstarted

  OpenTok Dev Mailing List:
  http://groups.google.com/group/opentok-developers

## Want to contribute?
### To run test suite:
    jasmine-node --coffee --autotest spec/
