## Approach to answering questions in the CKAD Exam

```diff
IMPORTANT
- At the top of each question, you may be given a command to set the current context. 👈👈👈
- Make sure to run it for each question as different questions will be in different clusters. 👈👈👈
```
<br />

1. Read the Question

- If you have no idea what they are asking or talking about, flag the question and move to the next question
<br />

2. If you understand the question:

- Chunk up the question and start identifying the order in which to create resources:
  - Namespaces first
  - ConfigMaps and Secrets next
  - Finally Deployments and Services
<br />

3. Try to create as many resources from the Command Line (imperative) as possible:

- Use the kubectl autocomplete to complete imperative commands
- Use the "-h" help flag to get examples
  - To get Deployment examples use: `kubectl create deploy -h`
  - To get Pod examples use: `kubectl run -h`
  - To create Services either use:
    - Expose: `kubectl expose -h` << This is faster as it does the label plumbing for you >>
    - Create: `kubectl create service -h`
- Use the example command lines to create as much of the skeleton YAML as possible
<br />

4. If you cannot satisfy the entire question from the command line output the file for editing:

- `--dry-run=client -o yaml > <my-file>.yml`
- When you create the YAML file, name the file after the question you are working on to aid in linking questions and YAML files for later review
<br />

5. When needed, use the [bookmarks](https://github.com/jamesbuckett/ckad-bookmarks) to obtain snippets of code to solve the question:

- Copy and paste the snippet code from the left edge to try to preserve indentation when you paste into the YAML file
<br />

6. Optional, you can check to see if the YAML file is valid by running: `kubectl apply -f my-file.yml --dry-run=client -o yaml`

- If the YAML is valid it will display some YAML in the terminal
- If the YAML has an indentation error you will get an error similar to this:
  - `error: error parsing /root/ckad/my-file.yml: error converting YAML to JSON: yaml: line 21: did not find expected key`
<br />

7. After applying the YAML file, please check your work:

- Run verification commands like:
  - `kubectl get all` to verify that Deployments are created, Pods are running
  - `kubectl get endpoints` to verify that the Service is load balancing to Pods
<br />

8.  If the your solution does not work try to troubleshoot if you think you know where the problem is:

- If a Pod is failing use these troubleshooting commands in this sequence:
  - What is the overall status in the namespace: `kubectl get all`
  - If the pod did not start look at the events related to the pod: `kubectl describe pod <problem-pod>`
  - If the pod did start but is not behaving as expected, look at it's logs: `kubectl logs <problem-pod>`
  - If you need to delete the pod with minimum delay use: `kubectl delete pod <problem-pod> --now`
  - If you do not solve the problem and you are not clear on what the problem is, move to the next question.

_End of Section_
