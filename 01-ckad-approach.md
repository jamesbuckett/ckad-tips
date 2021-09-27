## Approach to answering questions in the CKAD Exam

```diff
IMPORTANT
- At the top of each question, you may be given a command to set the current context.
- Make sure to run it for each question as different questions will be in different clusters.
```

1. Read the Question

- If you have no idea what they are asking or talking about, flag the question and move to the next question

2. If you understand the question:

- Chunk up the question and start identifying the order in which to create resources:
  - Namespaces first
  - ConfigMaps and Secrets next
  - Finally Deployments and Services

3. Try to create as many resources from the Command Line (imperative) as possible

- Use the "-h" help flag to get examples
  - To get Deployment examples use: `kubectl create deploy -h`
  - To get Pod examples use: `kubectl run -h`
  - To create Services either use:
    - Expose: `kubectl expose -h` << This is faster as it does the label plumbing for you >>
    - Create: `kubectl create service -h`
- Use the example command lines to create as much of the skeleton YAML as possible

4. If you cannot satisfy the entire question from the command line output the file for editing

- `--dry-run=client -o yaml > <my-file>.yml`
- When you create the YAML file, name the file after the question you are working on to aid in linking questions and YAML files for later review

5. Use the [bookmarks](https://github.com/jamesbuckett/ckad-bookmarks) to obtain a snippet of code that aids in solving the question

- Copy and paste the snippet code from the left edge to try to preserve indentation when you paste into the YAML file

6. Check your work

- Run verification commands like:
  - `kubectl get all` to verify that Deployments are created, Pods are running
  - `kubectl get endpoints` to verify that the Service is load balancing to Pods

7.  If the your solution does not work try to troubleshoot if you think you know where the problem is

- If a Pod is failing use these troubleshooting commands in this sequence:
  - What is the overall status in the namespace: `kubectl get all`
  - If the pod did not start look at the events related to the pod: `kubectl describe pod <problem-pod>`
  - If the pod did start but is not behaving as expected, look at it's logs: `kubectl logs <problem-pod>`
  - If you do not solve the problem and you are not clear on what the problem is, move to the next question.

_End of Section_
