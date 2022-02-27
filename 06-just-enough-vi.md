06-just-enough-vi.md

# Just Enough `vi`
* This is a light introduction to `vi`

## What is `vi`
* vi is a screen editor for Linux, Unix and other Unix-like operating systems
* Pronounced (vee-aye), vi stands for visual instrument

## Important `vi` concepts

* `vi` has two modes
    * `command mode` - issue vi commands such as deleting, copying, search and replace, saving
    * `insert mode` -  input or enter content into the file
      * You are in insert mode if you see `-- INSERT --` at the bottom of the file
      * If you are in `-- INSERT --` mode, use the `Esc` key to return to `command mode`

* You will be switching between these two modes while editing the file
  * In `command mode` perform common actions such as navigation, search and save
    * Once you are at the line you want to edit, you switch to `insert mode`
  * In `insert mode` make text changes to the file 
    * When done making changes you switch back to `command mode`  to save and exit

## `vi` examples

<details class="faq box"><summary>Create a sample configuration file</summary>
<p>

```bash
clear
# Using the best example that matches the question
mkdir -p ~/ckad/
kubectl run pod-1 --image=nginx --dry-run=client -o yaml > ~/ckad/01-02.yml
```

</p>
</details>

<details class="faq box"><summary>Open the configuration file for editing</summary>
<p>


```bash
clear
# To start editing a file with vi type vi and the location of the file to be edited 
# When you issue this command you are in "Command Mode"
vi ~/ckad/01-02.yml
```

<details class="faq box"><summary>Navigating a file in Vi</summary>
<p>

Navigation
* Arrow keys - move the cursor down, up, left and right (similar to the arrow keys)
* `^` (caret) - move cursor to beginning of current line
* `$` - move cursor to end of the current line
* `nG` - move to the nth line (eg 5G moves to 5th line)
* `G` - move to the last line

Command Mode: Shift+g - Move to last line
![18-shift-G](https://user-images.githubusercontent.com/18049790/155867216-862696b1-1083-41e1-96e8-6859c3d3ec1c.jpg)

Command Mode: Shift+$ - Move to end of line
![19-Shift-$-EOL](https://user-images.githubusercontent.com/18049790/155867218-790a825b-9c2b-4560-8352-2e169e1c03dc.jpg)

</p>
</details>

</p>
</details>

<details class="faq box"><summary>Replace one word in vi</summary>
<p>

Delete Content
* `x` - delete a single character
* `dd` - delete the current line

Command Mode: Arrow Keys [up,down,left,right]
![01-move-to-word](https://user-images.githubusercontent.com/18049790/155866903-18b6a733-1715-4897-a282-2ade9bb083af.jpg)


Command Mode: d+$ - Delete everything to end of line
![02-d$-to-eol](https://user-images.githubusercontent.com/18049790/155866904-519d794c-5aee-45ae-bac7-353c672de563.jpg)

Insert Mode: "a" - after start typing replacement text
![03-a-new-word](https://user-images.githubusercontent.com/18049790/155866905-2d6c03eb-db9d-4f66-929d-b0a8efecf008.jpg)

</p>
</details>

<details class="faq box"><summary>Replace one character in vi</summary>
<p>

Command Mode: Arrow Keys [up,down,left,right]
![04-replace-single-move-to](https://user-images.githubusercontent.com/18049790/155866906-56e21794-b043-44a9-9816-f58e6e8f6274.jpg)

Insert Mode: "r" - replace character cursor is at
![05-replace-single-move-to-R](https://user-images.githubusercontent.com/18049790/155866892-17097a03-218a-4b79-95d1-d1ce4bfa418c.jpg)

Command Mode: Esc+x - Escape key to return to command mode and "x" to save and quit
![06-replace-single-move-to-esc-x](https://user-images.githubusercontent.com/18049790/155866893-e9f9f8c8-2773-4bab-9c61-81cb77886c0b.jpg)

</p>
</details>


<details class="faq box"><summary>Search for a word in vi</summary>
<p>

Command Mode: /<string> - / = search + text=nginx
![07-slash-search](https://user-images.githubusercontent.com/18049790/155866894-b20a1540-ccb6-42eb-87c5-dbf6149a49db.jpg)

Command Mode: Enter key to find first occurrence of text
![08-slash-search-ENTER](https://user-images.githubusercontent.com/18049790/155866895-9a0a0777-50e8-4ef8-975d-af2a8b3efb06.jpg)

Command Mode: "n" - Find "next" occurrence of text
![09-slash-search-n](https://user-images.githubusercontent.com/18049790/155866896-23f20d1e-9173-43dd-8d84-c9fd37cd7cbb.jpg)

Command Mode: "N" - Find "previous" occurrence of text
![10-slash-search-N](https://user-images.githubusercontent.com/18049790/155866897-c05b4189-9180-41a9-8708-edbcdebc55cf.jpg)

</p>
</details>

<details class="faq box"><summary>Undo last action in vi</summary>
<p>

Notes
* `u` - Undo the last action (you may keep pressing u to keep undoing)
* `U` (Note: capital) - Undo all changes to the current line

Command Mode: Esc key to return to command mode
![11-pre-undo](https://user-images.githubusercontent.com/18049790/155866899-262c771e-1dd8-42d7-a250-c1f1016495c1.jpg)

Command Mode: :u - Lower case "u" to undo last action
![12-undo-u](https://user-images.githubusercontent.com/18049790/155866900-b20f0ea7-34a1-4815-b1e0-15d0a9b4b7e7.jpg)

Command Mode: dd - Delete line 
![13-undo-undone](https://user-images.githubusercontent.com/18049790/155866901-d6912f16-6733-4e6f-b534-d7b45de77f66.jpg)

</p>
</details>

<details class="faq box"><summary>Line Numbers in vi</summary>
<p>

Command Mode: Esc key to return to command mode then :set nu - set numbers
![16-line-numbers-nu](https://user-images.githubusercontent.com/18049790/155867154-1fc1a7e5-5b18-4f91-a102-a52c1ff7cd6a.jpg)

Command Mode: dd - Line numbers on left side used for error message if YAML indentation is incorrect
![17-line-numbers-nu-with-numbers](https://user-images.githubusercontent.com/18049790/155867155-b387752f-7d0d-44df-83bc-f6e4f8e59a7f.jpg)


</p>
</details>

<details class="faq box"><summary>Quit vi</summary>
<p>

Command Mode: Esc key to return to command mode then q! - quit without saving
![14-quit-with-out-save](https://user-images.githubusercontent.com/18049790/155867072-b7972203-4d7e-4a28-acea-0d10f5f123c7.jpg)


</p>
</details>

<details class="faq box"><summary>Save and Exit vi</summary>
<p>

Save and Quit
* `w` - write (save) file
* `q` - quit file
* `x` - write and quit file

Command Mode: Esc key to return to command mode then :x - Save and quit
![15-write-exit](https://user-images.githubusercontent.com/18049790/155867073-6d6ae69a-285e-4420-bea4-9a4c46fc6665.jpg)

</p>
</details>
<br />

