# audiostream
===============

Stream and transcode your music library.  The goal is to make software you want to use, for instance an itunes-like audio jukebox player experience in the browser.  HTML5 audio is tricky because not all browser's support all codecs/containers.  This app uses ffmpeg, a free open source media transcoder, to support all browsers.

## How to use

### Requirements
* Unix variant OS (OSX, Linux, BSD, etc.)
* [ffmpeg](http://ffmpeg.org/download.html)
* [Node.js](http://nodejs.org/download/)
* NPM

Currently only Unix like operating systems are supported for the server.  Windows support has not yet been tested.
You need to install ffmpeg and have it in your path so that typing `which ffmpeg` in your command line produces an absolute path.

### Download source
`$ git clone git://github.com/nickdesaulniers/audiostream.git && cd audiostream && npm install`

### Configure
Modify `config/config.json` to add your music library's absolute paths.  Notice how for paths with spaces, the spaces and parentheses needs to be escaped (a single backslash), and for JSON the escape character needs to be escaped (two backslashes).

### Run
`npm start` or `$ node app.js`

### View
`$ open localhost:3000`

## Notes
* Click on any link to fetch a file.  If the file has not yet been transcoded, it will be, then served, otherwise it serves the previously encoded version.  The encoded files will be in `library/`.
* The app currently transcodes a file (tested mp3's, and ogg's so far) to either ogg, mp3, aac, or wav based on browser support.  If the original format is supported, then that file is served, otherwise a preferred format is transcoded to and served.
* HTTP Basic Authentication is currently being used, for it's simplicity.  You can find the username and password in the `config/config.json` file.  You need to restart the server if you modify the config file.

## Contributing
* Bug reports are always welcome!  Please file them as issues on the github page: https://github.com/nickdesaulniers/audiostream/issues
* Do NOT just fork and send a pull request!!!  If there is an issue in the issue tracker that you want to tackle, and it has been accepted, feel free to to fork, and issue a pull request.  Otherwise, please first create an issue, and wait for it to be approved.  This will allow you to 'fail sooner,' as in have your patch declined before you write it, if it's not in line with the goals of this project.
  1. Is there an issue in the issue tracker you want to tackle, that has been accepted? If yes, goto 4.
  2. Create issue in the issue tracker, and wait for it to be accepted or declined.
  3. Was the issue declined?  If yes, goto 1.
  4. Fork.
  5. Write your patch.
  6. Pull Request.
  7. Was your pull request declined?  If yes, goto 5.  If no, thanks! and goto 1.

## Authors
* Nick Desaulniers

## Browser HTML5 audio container compatibility
http://html5doctor.com/html5-audio-the-state-of-play/#support