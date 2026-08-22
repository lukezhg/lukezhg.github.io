---
layout: post
title: "aiva chatbot with neo4j brain"
date: 2020-12-07 23:10
comments: true
categories: 
tags: 
---
###主教程
https://explosion.ai/blog/chatbot-node-js-spacy

###构建虚拟环境
https://virtualenv.pypa.io/en/latest/user_guide.html

    cd myproject
    virtualenv venv  
    source venv/bin/activate #进入
    deactivate #退出
    (venv) chunleizhang@Mac~/lib/aiva

###开启aiva
    npm start --debug

###编辑aiva设置文件

    vi config/default.json

###Start the bot

    npm start --debug

###neo4j brain  
开关neo4j服务  

    neo4j start
    neo4j stop


http://localhost:7474/browser/

https://neo4j.com/docs/getting-started/3.5/cypher-intro/load-csv/
LOAD CSV WITH HEADERS FROM "file:///persons.csv" AS csvLine
CREATE (p:Person {id: toInteger(csvLine.id), name: csvLine.name})

/usr/local/Cellar/neo4j/3.5.3/libexec/import


https://app.slack.com/client/THS32FKN0/D01FW5UR2EB


