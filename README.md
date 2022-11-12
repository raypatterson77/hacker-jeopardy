# hacker-jeopardy docker

A fork from [https://github.com/bsidesvi/hacker-jeopardy](https://github.com/bsidesvi/hacker-jeopardy) that runs the game inside a docker container.     

## Adding your questions

Game data goes in `data/`. There you should add round files (create a `<NUM>.round`
file) and questions in `Questions.cp`. The format is pretty self explanatory.
Check `data/` for an example.

## Running  

After adding your Questions build and run the docker container:

```
docker image build -t hacker_jeopardy .
docker run -p 5000:5000 hacker_jeopardy
```

Then open [localhost:5000/host](http://localhost:5000/host) and setup the game.    
The player's view ([localhost:5000](http://localhost:5000)) can be opened at any time.    
Nothing will be displayed until the game is started by
the host.

*NOTE*: In order to avoid dataloss due to a crash, hacker-jeopardy is backed by a
database where transactions are pushed when the hosts submit the points. This
has the flipside requiring games to be finalized before a new one can be
started. Make sure that you always push the "Game over" button before
reloading to start a new game.
