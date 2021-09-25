## Approach to answering questions in the CKAD Exam

- 1. Read the Question
  - If you have no idea what they are asking or talking about move to the next question
- 2. If you understand the question
  - Chunk up the question and start identifying the order in which to create resources
    - Namespaces first
    - ConfigMaps and Secrets next
    - Finally Deployments and Services
- 3. Try to create as many resources from the Command Line (imperative)
  - Use the "-h" help flag to get examples
  - Use the example command lines to create as much of the skeleton YAML as possible
- 4. If you cannot satisfy the entire question from the command line output the file for editing
- 5. Use the Bookmarks to obtain a snippet of code that solves the question
- 6. Check your work
  - Run verification commands like: kubectl get all to verify that Deployments are running

_End of Section_
