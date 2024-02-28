# ChatGPT-KGC-KGR
This repository presents the work of prompting ChatGPT to solve the tasks of Knowledge Graph Completion (KGC) and Knowledge Graph Reasoning (KGR) on both Static and Temporal KGs.
It's context is the work previously described in https://github.com/IonutIga/TOD-System, where a Task Oriented Dialogue System is defined, that uses an ontology to map the knowledge of a specific domain, a KG to map the conversation's context, and another one to store any information that is validated by the user. Here, one aspect of the local KG is tested, where the TODS has to build the discussed instance.
Three types of prompting techniques are used: Direct Prompting (no examples, no reasoning steps, Zero-Shot), In-Context Learning (One-Shot), and Chain of Thought (Zero- and One-shot). Before experimenting, preliminary questions were asked, to assess ChatGPT's knowledge about the topics at hand, such as:
1. Do you know what a Knowledge Graph is?
2. Do you know what a Temporal Knowledge Graph is?
3. Do you know what an ontology is, in the context of Knowledge Graphs?
4. Do you know what Turtle syntax is, in the context of Knowledge Graphs?
5. Do you know what a triple is, in the context of Knowledge Graphs?
6. Do you know how to extract triples from a natural language phrase, given a provided ontology in the Turtle syntax?
7. Do you know today's date?
8. Do you know today's time?
# Knowledge Graph Completion
The main subject of each task of KGC is to extract useful information in the form of triples, using the Turtle syntax, from an input phrase. Each phrase is based on a provided ontology which describes three concepts (Employee, Project, and Status) and relationships attached to them. Four types of phrases are formulated:
1. Simple phrase, ex. "Insert an employee with name as John and role as Scientist".
2. Complex phrase, ex. "I cannot find John on the employee's list. You should add him, he's our Scientist".
3. Misspelled word for the class type, ex "Ana is our emplyee. Add her, as CEO".
4. A class type that is not in the ontology, ex. "Rocket is so talented. It does the best job as a guide dog".
Each type of phrase was tested using each prompting technique, for three different chatting rounds. In each round, the prompt is asked three times. This approach tests the inter- and intra-conversation(s) deterministic behaviour of asking the same question. A total of 48 chats were obtained.
Furthermore, the capabilites of constructing Temporal KGs was tested. The simple phrase type was used, and each triple's relationship is labelled with a timestamp. More exactly, each relationship becomes an instance of its actual type, then two more temporal relationships are defined: startDate and endDate. The start date is either today's date (when the phrase is encountered) or a provided one. The end date is either "Now" (meaning it is still valid), or a provided one. For example, suppose we have the triple :Employee1 :hasName :John. The relationship :hasName will be instantiated as :hasName1 rdf:instanceOf :hasName. Then, the two temporal relationships are defined, as :hasName1 :startDate "20-02-2024", :hasName :endDate "Now", meaning the fact where :hasName1 is present is valid from 20-02-2024 until further notice.
# Knowledge Graph Reasoning
For the KGR task, ChatGPT was asked to respond to two simple questions, requiring information that is/is not temporally valid. 

