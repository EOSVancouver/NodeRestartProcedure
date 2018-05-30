# NodeRestartProcedure
Restart procedure for BP node

The restart sequence should roughly follow this approach:

1. just restart nodeos, ideally all of the data files are in a good state and nodeos starts running again.
2. if #1 fails try the --replay option, it runs pretty fast and rebuilds some of the files from the block logs that are already on your machine
3. if #2 fails try the --hard-replay option, it deletes the chain database (the shared_mem directory) and replays from the block log (the data directory)
4. as a last resort save a copy of your data directory and use the --resync option, it erases your local data files and pulls a copy of the current chain state from the network, this takes a lot of time and puts a larger load on the network


