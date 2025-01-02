Tue May 23 01:57:42 WITA 2023

# BloodSweatTears

ADD TO THE BOTTOM, NOT HERE!

### 9-09-21

1. `liver-server` is really really bad when changing CSS UNLESS it is started from a directory rather than .html file.

i.e. `~/something/something/ % live-server something/`

2. In order to create a new project on git via CLI git CLI is needed -
   `gh create repo ${name}` to create the remote via CLI.
   Then add all and commit push.

3. `Emmet` on nvim is used with a key combination rather than automatically.
   i.e. `M-y then ,` in my case.

4. `.tmux.config` will not load if the symlink is broken. Symlink should be created from the destination's folder i.e. `~% ln -s something/.dotfiles/.tmux.config .`

5. When tmux dies unexpectedly often, it might help to delete the tmux folder form `/temp/` folder.

6. A WAY better way to work with the command area of nvim is through `:ctrl f` which will open a nvim-like mini window to work on with the command area.

### 10-09-21

7. in css/html when the meta attribute fails to fill the screen with content in mobile, there is an option to use `min-width: fit-content` attribute.
8. iterm2 and tmux integratio works really well, if started from iterm2.
9. oh-my-zsh is needed for zsh plugins. a super important plugin is `autosuggestions`.
10. Always remember to add `__dirname` to the relative path for `res.sendFile` in express.

### 11+12-09-21

11. When working with `flex` and `CSS` always make sure there are no trailing `<br>`s that mess up the spacing.
12. ALWAYS check for html native tags before some other fancy stuff - e.g. `<input type='date'>` instead of a package.
13. Better to work with `CDN` rather than `npm` for better preformance (caching).
14. Put the JS `script`s at the bottom of the HTML to make sure UI loads before the packages.
15. `Promises` work differently and cannot be accessed synchoronisly. `then` has to be used, for example when calling a fetch API.
16. TBD Grid VS Flex.

### 19-09-21

17. in iterm2 when `option` key is defined as `meta` then `prefix C-b` which is in many cases a defualt would work out of the box.
18. `cd` in `FZF` would work only as part of `FZF` in shell (or in my case .zsh) so if it is not installed in .zsh it won't work at all.

### 20-09-21

19. Use a `.zshrc` to add commit push in one line:

```
function lazygit() {
    git add .
    git commit -a -m "$*"
    git push
}
```

### 26-09-21

20. Use `nvim -o \`fzf\` ` to edit a file found with fzf.
21. For Emmet shortcuts define ',' as the lead so tapping twice on ',' triggers emmet.
22. For commenting, use tcomment plug with `g+motion` or visual block mode with ctrl+v then add # to all lines (takes place only after typing ESC).

```
Explicit commenting/uncommenting:

    g<{motion}   :: Uncomment region
    g<c          :: Uncomment the current line
    g<b          :: Uncomment the current region as block

    g>{motion}   :: Comment region
    g>c          :: Comment the current line
    g>b          :: Comment the current region as block

In visual mode:

    gc           :: Toggle comments
    g>           :: Comment selected text
```

### 03-10-21

23. In Bash:

```

  main () {
    if [ "$1" != "" ]; then
        echo "One for $1, one for me."
    else
        echo "One for you, one for me."
    fi
  }
  # call main with all of the positional arguments
  main "$@"
```

- funcs don't need the argument passed to access it.
- args are accessed: $1 - $N.
- if ends with fi.

### 11-10-21

24. Pipe fzf results to any other bach command - rm for example:

```
fzf | xargs rm
```

25. In #REACT #JSX - to turn a boolean we can just assign it to the opposite:

```
chosenTask.isCompleted = !chosenTask.isCompleted;
```

### 12-10-21

26. Pass `fzf` args to `mv`:
    this will move whatever fzf finds to the example directory:

```
fzf |

while read fname
do
mv $fname Desktop/example/dir/things.md
done
```

### 18-10-21

27. Pass `fzf` args to `code` to open in VSCode:

```
code `fzf`
```

28. When coping a react project, we gotta do the `npm install` to get all the dependencies up and installed,
    and npm would know where to look for those if there exist a `package.json` file and the install is executed form
    the project's folder.

### 20-10-21:

29. The difference between `class Portfolio extends Component {` and `class Portfolio extends Component() {` is quite big!
    If there is no need to invoke the function/ component , then don't do it. tabnine adds the paranthesis sometimes!

### 15-07-22:

30. Spent at least one hour figuring out how to sign in to GitHub with VSCode - essentially, nothing worked besides deleting the PAT, creating a new one, creating a repo and trying to push --> then instead of password, use the PAT.

### 17-07-22:

31. For some time the page wasn't interactive , JS wouldn't work / breaks since it was trying to get DOM elements before the DOM loads.

The solution for this is either to add the `defer` attribute to the script tag or to put the script tag at the bottom of the HTML so it renders after the DOM loads.

### 13-08-22:

32. some `npm` packages work with `require(package)` and some only with `import package from 'package'`.)

33. `NODE` tip: in order to automatically refresh a node app , install and run the `nodemon` package.

### 15-08-22:

34. To test an API, install the Thunder Client Extension in VScode and configure parameters, API key, and headers.

### 19-08-22:

35. Start the project from setting up Express, so `npm init -y` and then typescript `yarn add typescript -D` - `-D` is for devDependencies so it is only available during the build time and locally.

36. When using express or other packages with TS, we need to install `yarn add @types/express` or generally: `yarn add @types/packageName` to get the type definitions.

37. Setting up MongoDB: setting up Mongodb Atlas: get connection string and store it in `.env` file. This is safer than storing it in the code.

38. When creating an endpoint, we can use it to test the DB connection with POST. For this we need to create a schema and a model. The schema is the structure of the data and the model is the way we interact with the data. For this we need to use the libraries `mongoose` and `dotenv`. doteenv is used to read the `.env` file.

    ```
    const dotenv = require('dotenv');
    dotenv.config();
    ```

### 23-08-22:

39. Notice that `require` is outdated and should be replaced with `import`. For eaxample:

```
import { Router } from 'express';
const router = Router();
```

40. When interacting with MongoDB, use the VScode extension `MongoDB Explorer` to see the data.

41. Remember that tutorials could be outdated, for example, `retult.ops` is not a thing anymore with mongodb, for the `insertOne` method.

42. Use this script to automatically update a cell in google sheets with the last edited time:

```
function onEdit() {
 var s = SpreadsheetApp.getActiveSheet();
 if( s.getName() == "2022Q3" ) { //checks that we're on the correct sheet
    let targetCell = s.getRange(5,10);
    let formattedDate = Utilities.formatDate(new Date(), "GMT+0", 'E MM/dd/yyyy');
    targetCell.setValue(formattedDate);
   };
 };

```

### 08-10-22:

40. Everything I learned today about REACT from Scrimba:

- React is composable - components can be children of each other. See:
  ![figure](https://i.ibb.co/J2x0ycd/image.png)

- React is declarative - we don't tell the browser how to do something, we tell it what to do.
- React is component based - we can create components and reuse them.

- JSX turns JS functions into React elements. It is a specific syntax for this purpose.

- Componenets can be bundled using fragments. Fragments are like empty divs that don't show up in the DOM.

- Components are named with PascalCase. They are functions that return JSX. We use the following line to render components: `ReactDOM.render(<Component />, document.getElementById('root'));`

- Vite is a bundler that is faster than webpack. It is used to bundle the code and make it ready for production. It comes of the shelf with npm and can be installed with `npm init vite@latest`. It is a zero config bundler.

- To start a project quickly, use vite as follows: `npm init vite@latest my-vite-app -- --template react` or just `npm init vite@latest` and then `npm install` and `npm run dev`.

### 12-04-23:

41. Create a global .gitignore and assign it to all projects automatically:

```
echo .DS_Store >> ~/.gitignore_global #this will add .DS_Store to the global gitignore
git config --global core.excludesfile ~/.gitignore_global #this will store the gitignore_global in the root folder and add it to all future projects

```

### 13-04-23

The fast and secure way to find which `.vimrc` or `init.vim` filr is used is by running:
`:echo $MYVIMRC`
Details:
https://stackoverflow.com/questions/8977649/how-to-locate-the-vimrc-file-used-by-vim

### 15-04-23

1. To search across the codebase with amazing preview:
   `Telescope live_grep`

2. Find and replace by pattern:
   `:%s/<search phrase>/<replace phrase>/options`
   where the `%` symbol applies to all occurrences in the file (can use without for first only).

### 17-04-23

1. Set up copilot on NVChad is a nightmare:
   1. Has to update in `init.lua`, plugins and custom. BTW `init.lua` is at `.config/nvim/init.lua`
   2. Then has to sync NVChad through the NVdashboard.
   3. Then needs to set lazyload to false for it to work for some reason.

### 19-05-23

1. The mapping definitions for iterm2 and NVChad get mixed and this is a nightmare
   for alt specifically, defined as <M> or <A> in mapping settings.
   The only way to make it work right is to define it in iterm2 settings as the default (which is +esc for option key)..

### 29-06-23

1. Packer is the package manager I'm using and I always forget for #NVIM.
2. To jump a full paragraph `}` and `{` is very handy.
   . The very helpful status line I'm using is called Airline.

### 17-08-24

1. #Python - to effectively run jupyter notebook (inside Cursor / VScode or not) the desired follow should be:

- in terminal create an env with venv as follows: `python3 -m venv env_name` and start it with `source env_name/bin/activate` .
- Then in that env don't forget to install `ipkernel` and `jupyter` so it will be able to be seen as a kernel from the notebook.
- Choose that kernel.
- install dependencies with `pip install` inside that env.

### 27-12-24
- 1. Undefined is better than null or an empty string:
    1. Optional type is defaulted to undefined in typescript.
   ![how to fallback to undefined](../assets/2.jpg


### 28-12-24

- [vim] move screen up and down: zz , zt, z



### 01-01-25

- [vim] to surround a line with an HTML tag:
```
VSt<tag>
```
<pre>
V- visual mode to select the line
S- surround full sentence
t- for tag
</pre>
