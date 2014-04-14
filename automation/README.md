# Automation

The less work you have to do when performing repetitive tasks like minification, compilation, unit testing, linting, etc, the easier your job becomes.

The main task that need to be carried out for best practices are:

* CSS Minification & Concatenation
* Javascript Minification & Concatenation
* Javascript Validation
* SASS & Compass Compiling
* Image minification
* Auto generated icons CSS
* CSS Autoprefixing
* Live Reload

Our .NET setup takes care of minification & concatenation by bundling files together of our choice. 

Grunt.js is an ideal task runner to address thes remaining repetive tasks.
Here are plugins we make use of:

* JSHint - Validate Javascript files
* SASS - Compile Sass to CSS
* Imagemin - Minify PNG, JPEG and GIF images
* Autoprefixer - Parses CSS and adds vendor-prefixed CSS properties using the Can I Use database
* Watch - Run tasks, moved to the tasks folder
* Connect - Live Reload

## Getting started with Grunt.js

Grunt and Grunt plugins are installed and managed via npm, the Node.js package manager.

Grunt 0.4.x requires stable Node.js versions >= 0.8.0. Odd version numbers of Node.js are considered unstable development versions. You can download in here: `http://nodejs.org/`

### Installing the CLI

In order to get started, you'll want to install Grunt's command line interface (CLI) globally. You may need to use sudo (for OSX, *nix, BSD etc) or run your command shell as Administrator (for Windows) to do this.

``` linux
npm install -g grunt-cli
```

This will put the grunt command in your system path, allowing it to be run from any directory.

Note that installing grunt-cli does not install the Grunt task runner! The job of the Grunt CLI is simple: run the version of Grunt which has been installed next to a Gruntfile. This allows multiple versions of Grunt to be installed on the same machine simultaneously.

### How the CLI works

Each time grunt is run, it looks for a locally installed Grunt using node's require() system. Because of this, you can run grunt from any subfolder in your project.

If a locally installed Grunt is found, the CLI loads the local installation of the Grunt library, applies the configuration from your Gruntfile, and executes any tasks you've requested for it to run.

To really understand what is happening, read the code. It's very short.

### Working with an existing Grunt project

Grunt projects require the `package.json` and `Gruntfile.js` files to be added to the root folder of the project. A boilerplate of these 2 file files be found below.

Assuming that the Grunt CLI has been installed and that the project has already been configured with a package.json and a Gruntfile, it's very easy to start working with Grunt:

1. Change to the project's root directory.
2. Install project dependencies with `npm install`.
3. Run Grunt with `grunt`.

That's really all there is to it. Installed Grunt tasks can be listed by running grunt --help but it's usually a good idea to start with the project's documentation.

####Gruntfile.js Boilerplate

```js
/** 
* Grunt Boilerplate
*/

module.exports = function(grunt) {

  grunt.initConfig({
    pkg: grunt.file.readJSON('package.json'),

    imagemin: {
      dist: {
        options: {
          cache: false
        },
        files: [{
          expand: true,
          cwd: 'img/',
          src: ['*.{png,jpg,gif}'],
          dest: 'img/'
        }]
      }
    },
    
    jshint: {
      all: 'js/*.js'
    },

    sass: {
      dist: {
        options: {
          style: 'nested'
        },
        files: {
          'css/style.css': 'css/style.scss'
        }
      }
    },

    autoprefixer: {
      dist: {
        files: {
          'css/style.auto.css': 'css/style.css'
        }
      }
    },

    watch: {
      options: {
        livereload: true,
      },

      js: {
        files: 'js/**/*.js',
        tasks: ['jshint'],
        options: {
          spawn: false,
        }
      },

      css: {
        //directory path and it's subdirectories,
        files: ['css/**/*.scss'],
        tasks: ['sass', 'autoprefixer'],
        options: {
          spawn: false,
        }
      },

      images: {
        files: ['img/**/*.{png,jpg,gif}', 'img/*.{png,jpg,gif}'],
        tasks: ['img'],
        options: {
          spawn: false,
        }
      },

      html:{
        files: ['./**/*.html'],
        tasks: [],
        options: {
          spawn: false
        }
      }
    },

    server: {
      options: {
        port: 8000,      
        base: './'
      }
    },

  });

  // Load the plugin(s).
  grunt.loadNpmTasks('grunt-contrib-imagemin');
  grunt.loadNpmTasks('grunt-contrib-jshint');
  grunt.loadNpmTasks('grunt-contrib-sass');
  grunt.loadNpmTasks('grunt-autoprefixer');
  grunt.loadNpmTasks('grunt-contrib-watch');
  grunt.loadNpmTasks('grunt-contrib-connect');

  // Default task(s).
  grunt.registerTask('default', ['imagemin','jshint','sass','autoprefixer','watch','connect']);
  // grunt.registerTask('dev', []); Look into DEV register task

};

```
####package.json Boilerplate

```json
{
  "name": "my-project-name",
  "version": "0.1.0",
  "devDependencies": {
    "grunt": "^0.4.4",
    "grunt-contrib-jshint": "~0.6.3",
    "grunt-contrib-sass": "~0.6.0",
    "grunt-contrib-watch": "~0.5.3",
    "grunt-contrib-imagemin": "~0.5.0",
    "grunt-autoprefixer": "~0.6.5",
    "grunt-contrib-connect": "^0.7.1"
  }
}
```


