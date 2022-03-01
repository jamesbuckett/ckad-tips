06-just-enough-vi.md

# Just Enough vi
* This is an introduction to `vi` to assist you in preparing for the CKAD exam

## What is vi
* vi is a screen editor for Linux, Unix and other Unix-like operating systems
* Pronounced (vee-aye), vi stands for visual instrument
* [vi](https://en.wikipedia.org/wiki/Vi) and [vim](https://en.wikipedia.org/wiki/Vim_(text_editor)) are interchangeable
* The examples below work for both vi and vim

## Important vi/vim concepts

* `vi` has two modes
    * `command mode` - issue commands such as deleting, copying, saving and search and replace
    * `-- INSERT -- mode` -  paste text or edit the file
      * You are in insert mode if you see `-- INSERT --` at the bottom of the file
      * If you are in `-- INSERT --` mode, use the `Esc` key to return to `command mode`

* You will be switching between these two modes while editing the file
  * In `command mode` perform common actions such as navigation, search and save
    * Once you are at the line you want to edit, you switch to `-- INSERT -- mode`
  * In `-- INSERT -- mode` make text changes to the file 
    * When done making changes you switch back to `command mode`  to save and exit

## vi/vim examples

<details class="faq box"><summary>Create a sample configuration file</summary>
<p>

```bash
clear
mkdir -p ~/ckad/
kubectl run pod-1 --image=nginx --dry-run=client -o yaml > ~/ckad/01-02.yml
```

</p>
</details>

<details class="faq box"><summary>Open the file with vi</summary>
<p>

Notes
* To start editing a file with `vi` type `vi` and the location of the file to be edited 
* When you issue this command you are in automatically in `command mode` when the file opens

```bash
clear
vi ~/ckad/01-02.yml
```

<details class="faq box"><summary>Navigating a file in vi</summary>
<p>

Navigation - While in `command mode`
* Arrow keys - move the cursor down, up, left and right 
* `^` (caret) - move cursor to beginning of current line
* `$` - move cursor to end of the current line
* `nG` - move to the nth line (eg 5G moves to 5th line)
* `G` - move to the last line

In `command mode`: `Shift+g` = Move to last line
![18-shift-G](https://user-images.githubusercontent.com/18049790/155867216-862696b1-1083-41e1-96e8-6859c3d3ec1c.jpg)

In `command mode`: `Shift+$` = Move to end of line
![19-Shift-$-EOL](https://user-images.githubusercontent.com/18049790/155867218-790a825b-9c2b-4560-8352-2e169e1c03dc.jpg)

</p>
</details>

</p>
</details>

<details class="faq box"><summary>Replace one word in vi</summary>
<p>

Notes
* This will be the majority activity for the CKAD exam
* Replacing a word in a configuration file

Delete Content - While in `command mode`
* `d$` - delete to end of line
* `x` - delete a single character
* `dd` - delete the current line

In `command mode`: Arrow Keys [up,down,left,right]
![01-move-to-word](https://user-images.githubusercontent.com/18049790/155866903-18b6a733-1715-4897-a282-2ade9bb083af.jpg)

In `command mode`: `d+$` - Delete everything to end of line
![02-d$-to-eol](https://user-images.githubusercontent.com/18049790/155866904-519d794c-5aee-45ae-bac7-353c672de563.jpg)

In `-- INSERT -- mode` : `a` = "after" this position, start typing replacement text
![03-a-new-word](https://user-images.githubusercontent.com/18049790/155866905-2d6c03eb-db9d-4f66-929d-b0a8efecf008.jpg)

</p>
</details>

<details class="faq box"><summary>Replace one character in vi</summary>
<p>

Notes
* Sometimes you only need to change a single character in a configuration file such as number of replicas
* Use the (r)eplace function to replace a single character 

In `command mode`: Arrow Keys [up,down,left,right]
![04-replace-single-move-to](https://user-images.githubusercontent.com/18049790/155866906-56e21794-b043-44a9-9816-f58e6e8f6274.jpg)

In `-- INSERT -- mode`: `r` = "replace" the character the cursor is at
![05-replace-single-move-to-R](https://user-images.githubusercontent.com/18049790/155866892-17097a03-218a-4b79-95d1-d1ce4bfa418c.jpg)

In `command mode`: `Esc+x` - Escape key to return to command mode and `x` to save and quit
![06-replace-single-move-to-esc-x](https://user-images.githubusercontent.com/18049790/155866893-e9f9f8c8-2773-4bab-9c61-81cb77886c0b.jpg)

</p>
</details>

<details class="faq box"><summary>Paste a block of text in vi</summary>
<p>

Notes - This is an important section
* A few of the questions in the CKAD exam involve pasting a code snippet into a configuration file 
* Copy the code snippet from the left border of the web page
* Use arrow keys to move to where you want to paste the code snippet
* Once you have verified that you are at the correct section for the paste 
* Shift `$` to move to the end of the line 
* Type `a` to paste text "after" and puts you into `-- INSERT -- mode`
* `Enter` key to create an empty line for the paste
* Paste the code snippet into the file usually with Mouse Paste
* Fix any indentation if required

</p>
</details>


<details class="faq box"><summary>Search for a word in vi</summary>
<p>

Notes - This is an important section
* A majority of the questions in the CKAD exam involve editing a configuration file and making a change to match the requirements from the question
* Use the search(/) command to quickly find the text that needs to be changed in the configuration file

In `command mode`: `/<string>` = search + text (in this example search for "nginx")
![07-slash-search](https://user-images.githubusercontent.com/18049790/155866894-b20a1540-ccb6-42eb-87c5-dbf6149a49db.jpg)

In `command mode`: `Enter` key to find first occurrence of text
![08-slash-search-ENTER](https://user-images.githubusercontent.com/18049790/155866895-9a0a0777-50e8-4ef8-975d-af2a8b3efb06.jpg)

In `command mode`: `n` - Find "next" occurrence of text
![09-slash-search-n](https://user-images.githubusercontent.com/18049790/155866896-23f20d1e-9173-43dd-8d84-c9fd37cd7cbb.jpg)

In `command mode`: `N` - Find "previous" occurrence of text
![10-slash-search-N](https://user-images.githubusercontent.com/18049790/155866897-c05b4189-9180-41a9-8708-edbcdebc55cf.jpg)

</p>
</details>

<details class="faq box"><summary>Undo last action in vi</summary>
<p>

Troubleshooting
* You may encounter an error while editing a file, such a cut and paste operation that goes wrong
* You can undo the last action with these commands
  * `:u` - Undo the last action (you may keep pressing u to keep undoing) #👈👈👈 This is the preferred option to undo a bad paste operation
  * `:U` (Note: capital) - Undo all changes to the current line

In `command mode`: `Esc` key to return to command mode
![11-pre-undo](https://user-images.githubusercontent.com/18049790/155866899-262c771e-1dd8-42d7-a250-c1f1016495c1.jpg)

In `command mode`: `:u` - Lower case "u" to undo last action
![12-undo-u](https://user-images.githubusercontent.com/18049790/155866900-b20f0ea7-34a1-4815-b1e0-15d0a9b4b7e7.jpg)

In `command mode`: `dd` - Delete line 
![13-undo-undone](https://user-images.githubusercontent.com/18049790/155866901-d6912f16-6733-4e6f-b534-d7b45de77f66.jpg)

</p>
</details>

<details class="faq box"><summary>Line Numbers in vi</summary>
<p>

Troubleshooting
* You may have an indentation problem with your file
* When you pass the file to the API server you may get an error message similar to this
  * `error: error parsing /root/ckad/my-file.yml: error converting YAML to JSON: yaml: line 21: did not find expected key`
* Use the Line Numbers option to quickly find the offending line to fix the indentation

In `command mode`: `Esc` key to return to command mode then `:set nu` = set numbers
![16-line-numbers-nu](https://user-images.githubusercontent.com/18049790/155867154-1fc1a7e5-5b18-4f91-a102-a52c1ff7cd6a.jpg)

In `command mode`: Line numbers on left side used for error message if YAML indentation is incorrect
![17-line-numbers-nu-with-numbers](https://user-images.githubusercontent.com/18049790/155867155-b387752f-7d0d-44df-83bc-f6e4f8e59a7f.jpg)

</p>
</details>

<details class="faq box"><summary>Quit without saving in vi</summary>
<p>

Troubleshooting
* Sometimes you may make get to a catastrophic state with the file that you are editing
* In cases such as this it is better to quit and start again
* Use this nuclear option to quit the file without saving to start over with the file

In `command mode`: `Esc` key to return to command mode then `q!` = quit without saving
![14-quit-with-out-save](https://user-images.githubusercontent.com/18049790/155867072-b7972203-4d7e-4a28-acea-0d10f5f123c7.jpg)


</p>
</details>

<details class="faq box"><summary>Save and Exit vi</summary>
<p>

Save and Quit in `command mode`
* `:w` - write (save) file
* `:q` - quit file
* `:wq` - write and quit file
* `:x` - write and quit file #👈👈👈 This is the preferred option as it is the least keystrokes

In `command mode`: `Esc` key to return to command mode then `:x` = Save and quit
![15-write-exit](https://user-images.githubusercontent.com/18049790/155867073-6d6ae69a-285e-4420-bea4-9a4c46fc6665.jpg)

</p>
</details>
<br />