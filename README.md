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

language: node_js

node_js:

  - "stable"
  
cache:

  directories:
  
  - node_modules
  
script:

  - npm test
  
  - npm run build
  
deploy:

  provider: pages
  
  skip_cleanup: true
  
  github_token: $ <span style="color:red">github_token_5</span>
  local_dir: build
  
  on:
  
branch: master



