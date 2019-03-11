Install funny stuff:
 > sudo npm8 install react react-dom react-script create-react-app

Create app, bevare errors, lets use the old npx here, for stability
 > npx8 create-react-app greens_pages
alternatives here https://github.com/facebook/create-react-app

Lets check that it works:
 > cd greens_pages
 > npm start
 > firefox http://localhost:3000/

Git stuff
 > git init
It should occur that it is already initialized
Create empty repo:
 > curl -u 'flmath' https://api.github.com/user/repos -d '{"name":"greens_pages"}'
 > git remote set-url --add origin https://github.com/flmath/greens_pages.git
 > git push --set-upstream origin master
 
reference https://gist.github.com/alexpchin/dc91e723d4db5018fef8

add travis.yml
```yml
language: node_js
node_js:
   - "11.10.1"  
#  - "stable"
# Stable nodejs has bug: https://github.com/facebook/jest/issues/8069
cache:
  directories:
  - node_modules
  
script:
  - npm test 
  - npm run build
  
deploy:
  provider: pages 
  skip_cleanup: true
  github_token: $github_token_5
  local_dir: build

  on:  
branch: master
```

Modify package.json
```json

30 lines (29 sloc) 592 Bytes
{
  "name": "greens_pages",
  "version": "0.1.0",
  "private": true,
  "homepage": "https://flmath.github.io/greens_pages/",
  "dependencies": {
    "react": "16.8.3",
    "react-dom": "16.8.3",
    "react-scripts": "2.1.5"
  },
  "scripts": {
    "start": "react-scripts start",
    "build": "react-scripts build",
    "test": "react-scripts test",
    "eject": "react-scripts eject"
  },
  "eslintConfig": {
    "extends": "react-app"
  },
  "browserslist": [
    ">0.2%",
    "not dead",
    "not ie <= 11",
    "not op_mini all"
  ],
  "devDependencies": {
    "gh-pages": "^2.0.1"
  }
}
```
Generate token in github:

https://github.com/settings/tokens -> Generate new token

Github token description: github_token_5
Choose all repo options

Generate token
Save the hash!!!

Set token in travis.
Go to https://travis-ci.org/ and sign with github
Swith on green_pages and go to settings.
Add in Environment Variables: github_token_5 token hash

Synchronize package-lock with package
 > npm8 install 
 > git commit
 > git push
 
