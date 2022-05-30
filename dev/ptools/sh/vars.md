## _ Bash variables and scripts _

What really makes a "shell script" is a **shebang** that calls the necessary _interpreter_.
Not the _extension_, for sure.

_To locate my interpreter, I use "which" to get its PATH._

```bash
$ which bash
```

**TIP:** **Use** and **reference** variables in _your scripts._

### _ Environment Variables _

Usually exist in all CAPS.

```bash
echo "$USER $HOME $HISTCONTROL $TERM"
```

To see their values, we use _echo_. Refer them in scripts.
**Find them in `$ env` command**

### _ User Variables in Your Shell Environment _

Shell environment variables are set knownly in all CAPS as well.
Include double quotes for strings, well.
Notice there's no space around the assignment operator.
Don't you dare put any spaces there!

```bash
FIRSTNAME="Satish"
env | grep -i firstname # not in the env
export FIRSTNAME # export so that it's available to the env
env | grep -i firstname # it's here!

export FIRSTNAME="Satish" # one-liner
```

**Scenario:**
While logging into a MySQL database, I might set a variable for the password.

```bash
export TODAYSDATE=`date`
```

Use **backticks** to store a _command's output_ in a variable. 

Once the shell exits, the bash shell's environment and variables are lost.
A shell script is launched in a new instance of bash shell and thus it happens.
