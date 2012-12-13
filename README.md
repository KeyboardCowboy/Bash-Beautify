Bash Beautify, 2.x-DEV (NOT STABLE)
================================================================================
Version 2.x supports SVN 1.7 and higher.
--------------------------------------------------------------------------------

Bash Beautify adds simple color support and SVN and GIT branch recognition to
your bash prompt.

### Requirements
--------------------------------------------------------------------------------
- If using SVN, your project must use a standard `/trunk /branches /tags`
  structure.

### Installation
--------------------------------------------------------------------------------
1. Place the .bash_beautify file in your home directory.
2. Add the following line to the top of your .bash_profile or .bashrc file.

      `source ~/.bash_beautify`

That's it!  The next time you start a bash session you should see a pretty, new
bash prompt.

By default GIT branches are green and SVN are yellow.

If you would like to customzize your prompt, add the following line
under the previous one and use the brief tutorial below. (It might be helpful to
copy the one from the bottom of the actual file to start.)

    export PS1="[\u@\h]\$"

### Building Your Bash Prompt
--------------------------------------------------------------------------------
The bash prompt is really just a string with a few variables in it.  Here is a
list of the basic variables you can use and how they work:

#### UNIX COMMANDS
-------------
These will be replaced with their respective values.

    \u    Your username. (ex. calbrecht)
    \h    Your system hostname. (ex. localhost)
    \w    Your present working directory. (ex. /var/www/htdocs/website)

#### COLORS
------
These will alter the color of the text from this point forward.  Use the reset
at the bottom to stop using the changed color.

    ${BLACK}
    ${RED}
    ${GREEN}
    ${YELLOW}
    ${BLUE}
    ${VIOLET}
    ${CYAN}
    ${WHITE}
    ${BRIGHT_BLACK}
    ${BRIGHT_RED}
    ${BRIGHT_GREEN}
    ${BRIGHT_YELLOW}
    ${BRIGHT_BLUE}
    ${BRIGHT_VIOLET}
    ${BRIGHT_CYAN}
    ${BRIGHT_WHITE}
    ${NORMAL}
    ${RESET}

#### SVN and GIT
-----------
The icing on the cake.  Add this variable to your line and it will be replaced
with "(GIT_BRANCH|SVN_BRANCH)" depending on which (or both if you are crazy
enough) version control system you are using.

    $(vcs_branch)

### Examples
--------------------------------------------------------------------------------
1. A basic prompt.

      [calbrecht@localhost]$
      export PS1="[\u@\h]\$"


2. Add the present working directory to each prompt.

      [calbrecht@localhost: /var/www/htdocs/newsite/includes]$
      export PS1="[\u@\h: \w]\$"


3. Put the VCS branches in it.

      [calbrecht@localhost(7.x-1.x): /var/www/htdocs/newsite/includes]$
      export PS1="[\u@\h$(vcs_branch): \w]\$"


4. Spice it up with a little color.

      [calbrecht@localhost(7.x-1.x): /var/www/htdocs/newsite/includes]$
      export PS1="${BRIGHT_CYAN}[${CYAN}\u${BRIGHT_WHITE}@${CYAN}\h${WHITE}\$(vcs_branch)${WHITE}: \w${BRIGHT_CYAN}]${NORMAL}\$ ${RESET}"


### Advanced
--------------------------------------------------------------------------------
If you don't like the colors of the SVN and GIT branches, you can change those
in the .bash_beautify file in the vcs_branches function.  I coded them in there
to make it easier to deploy for newbies.

You can also call either piece separately without any formatting:

    $(git_branch)
    $(svn_branch)
