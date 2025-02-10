# buzzline-04-stonerogers
Streaming Data, Project 4
Melissa Stone Rogers, [GitHub](https://github.com/meldstonerogers/buzzline-04-stonerogers)

## Introduction

This is a professional project using matplotlib's animation capabilities to visualize streaming data. This project uses Apache Kafka to create uniquie JSON and CSV producers and consumers to simulate streaming data. Python Version 3.11.6 was used, as well as Git for version control. 
This project was forked from Dr. Case's project repository found [here](https://github.com/denisecase/buzzline-04-case). Much of the detailed instructions in this README.md were borrowed from Dr. Case's project specifications, and updated for my machine.
Commands were used on a Mac machine running zsh. 

We can analyze and visualize different types of streaming data as the information arrives.

This project generates four applications:

1. A basic producer and consumer that exchange information via a dynamically updated file. 
2. A JSON producer and consumer that exchange information via a Kafka topic. 
3. A CSV producer and consumer that exchange information via a different Kafka topic. 
4. A custom consumer that modifies existing code to visulize a specific insight (Task 8). 

All four applications produce live charts to illustrate the data. 

## Task 1. Use Tools from Module 1 and 2

Before starting, ensure you have first completed the setup tasks in [Project 1](https://github.com/denisecase/buzzline-01-case) and [Project 2](https://github.com/denisecase/buzzline-02-case), created by Dr. Case. 
Python 3.11 is required. 

## Task 2. Copy This Example Project and Rename

Once the tools are installed, copy/fork this project into your GitHub account and create your own version of this project to run and experiment with.
Name it `buzzline-04-yourname` where yourname is something unique to you.
Follow the instructions in [FORK-THIS-REPO.md](https://github.com/denisecase/buzzline-01-case/docs/FORK-THIS-REPO.md).

## Task 3. Manage Local Project Virtual Environment

Follow the instructions in [MANAGE-VENV.md](https://github.com/denisecase/buzzline-01-case/docs/MANAGE-VENV.md) to:
1. Create your .venv
2. Activate .venv
3. Install the required dependencies using requirements.txt.

```zsh
python3.11 -m venv .venv
source .venv/bin/activate
```
```zsh
python -m pip install --upgrade pip setuptools wheel
python -m pip install --upgrade -r requirements.txt

```

Remember, each time a new terminal is opened, activate the .venv. 
```zsh
source .venv/bin/activate
```

### Initial Project Commit 
Turn on the autosave function in VS Code. Push changes to GitHub freqently to effectively track changes. Update the commit message to a meaningful note for your changes. 
```zsh
git add .
git commit -m "initial"                         
git push origin main
```

## Task 4. Start Zookeeper and Kafka (2 Terminals)

If Zookeeper and Kafka are not already running, you'll need to restart them.
See instructions at [SETUP-KAFKA.md] to:

1. Start Zookeeper Service ([link](https://github.com/denisecase/buzzline-02-case/blob/main/docs/SETUP-KAFKA.md#step-7-start-zookeeper-service-terminal-1))
### Start Zookeeper Service (Terminal 1)

```zsh
cd ~/kafka
chmod +x zookeeper-server-start.sh
bin/zookeeper-server-start.sh config/zookeeper.properties
```

Keep this terminal open while working with Kafka.

2. Start Kafka ([link](https://github.com/denisecase/buzzline-02-case/blob/main/docs/SETUP-KAFKA.md#step-8-start-kafka-terminal-2))

### Start Kafka (Terminal 2)
```zsh
cd ~/kafka
chmod +x kafka-server-start.sh
bin/kafka-server-start.sh config/server.properties
```
Keep this terminal open while working with Kafka. 
---

## Task 5. Start a Basic (File-based, not Kafka) Streaming Application

This will take two terminals:

1. One to run the producer which writes to a file in the data folder. 
2. Another to run the consumer which reads from the dynamically updated file. 

### Producer Terminal

Start the producer to generate the messages. 

In VS Code, open a NEW terminal.
Use the commands below to activate .venv, and start the producer. 

```zsh
source .venv/bin/activate
python3 -m producers.basic_json_producer_case
```

### Consumer Terminal

Start the associated consumer that will process and visualize the messages. 

In VS Code, open a NEW terminal in your root project folder. 
Use the commands below to activate .venv, and start the consumer. 

```zsh
source .venv/bin/activate
python3 -m consumers.basic_json_consumer_case
```

When done, remember to kill the associated terminals for the producer and consumer. 
---

## Task 6. Start a (Kafka-based) JSON Streaming Application

This will take two terminals:

1. One to run the producer which writes to a file in the data folder. 
2. Another to run the consumer which reads from the dynamically updated file. 

### Producer Terminal

Start the producer to generate the messages. 

In VS Code, open a NEW terminal.
Use the commands below to activate .venv, and start the producer. 

```zsh
source .venv/bin/activate
python3 -m producers.json_producer_case
```

### Consumer Terminal

Start the associated consumer that will process and visualize the messages. 

In VS Code, open a NEW terminal in your root project folder. 
Use the commands below to activate .venv, and start the consumer. 

```zsh
source .venv/bin/activate
python3 -m consumers.json_consumer_case
```

When done, remember to kill the associated terminals for the producer and consumer. 

## Task 7. Start a (Kafka-based) CSV Streaming Application

This will take two terminals:

1. One to run the producer which writes to a file in the data folder. 
2. Another to run the consumer which reads from the dynamically updated file. 

### Producer Terminal

Start the producer to generate the messages. 

In VS Code, open a NEW terminal.
Use the commands below to activate .venv, and start the producer. 

```zsh
source .venv/bin/activate
python3 -m producers.csv_producer_case
```

### Consumer Terminal

Start the associated consumer that will process and visualize the messages. 

In VS Code, open a NEW terminal in your root project folder. 
Use the commands below to activate .venv, and start the consumer. 

```zsh
source .venv/bin/activate
python3 -m consumers.csv_consumer_case
```

When done, remember to kill the associated terminals for the producer and consumer. 

---
## Task 8. Custom Consumer File 
This custom consumer file (project_consumer_stonerogrs.py) will use the existing json_producer_case.py producer file. The custom consumer will read from a Kafka topic and will focus on the sentiment of messages produced. A pie chart will be used to visualize the varying sentiment of messages. 

This will take two terminals:

1. One to run the producer which writes to a file in the data folder. 
2. Another to run the consumer which reads from the dynamically updated file. 

### Producer Terminal

Start the producer to generate the messages. 

In VS Code, open a NEW terminal.
Use the commands below to activate .venv, and start the producer. 

```zsh
source .venv/bin/activate
python3 -m producers.json_producer_case
```

### Consumer Terminal

Start the associated consumer that will process and visualize the messages. 

In VS Code, open a NEW terminal in your root project folder. 
Use the commands below to activate .venv, and start the consumer. 

```zsh
source .venv/bin/activate
python3 -m consumers.project_consumer_stonerogers
```

When done, remember to kill the associated terminals for the producer and consumer. 

---

## Possible Explorations

- JSON: Process messages in batches of 5 messages.
- JSON:Limit the display to the top 3 authors.
- Modify chart appearance.
- Stream a different set of data and visualize the custom stream with an appropriate chart. 
- How do we find out what types of charts are available? 
- How do we find out what attributes and colors are available?

---

## Later Work Sessions
When resuming work on this project:
1. Open the folder in VS Code. 
2. Start the Zookeeper service.
3. Start the Kafka service.
4. Activate your local project virtual environment (.env).

## Save Space
To save disk space, you can delete the .venv folder when not actively working on this project.
You can always recreate it, activate it, and reinstall the necessary packages later. 
Managing Python virtual environments is a valuable skill. 

### Final Project Commit 
Insure all final changes are committed to GitHub.
```zsh
git add .
git commit -m "final"                         
git push origin main
```

## License
This project is licensed under the MIT License as an example project. 
You are encouraged to fork, copy, explore, and modify the code as you like. 
See the [LICENSE](LICENSE.txt) file for more.

## Live Chart Examples

Live Bar Chart (JSON file streaming)

![Basic JSON (file-exchange)](images/live_bar_chart_basic_example.jpg)

Live Bar Chart (Kafka JSON streaming)

![JSON (Kafka)](images/live_bar_chart_example.jpg)

Live Line Chart with Alert (Kafka CSV streaming)

![CSV (Kafka)](images/live_line_chart_example.jpg)

