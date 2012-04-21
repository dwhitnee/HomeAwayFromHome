source ~/.functions

export PROMPT=" %m.$USER> "              # tcsh hostname

export PATH=/usr/local/bin/:/usr/local/sbin:$PATH:/opt/local/bin:/usr/local/mysql/bin

export EDITOR=emacs
export JAVA_HOME=/Library/Java/Home

export HISTSIZE=1000
export SAVEHIST=1000
export HISTFILE=~/.history

setopt ignoreeof
setopt noclobber                       # don't clobber files w/redirection(>)
#setopt savehist=100

alias ls="ls -CF"
alias ll="ls -l"
alias m="more"
alias k="exit"
alias rm="rm -i"
alias mv="/bin/mv -i"                   # prompting move
alias cp="/bin/cp -i"                   # prompting copy
alias du="du -kh"

alias h="history 10"                    # brief histroy
alias gerp="grep"
alias gep="grep"

# lose all temps and old files
#alias cleanup 'rm *.BAK *.o .*~ *~ ,* #*#; /bin/rm core'
alias cleanup='find . -name "*~" | xargs rm'

#alias cd 'cd \!* ; echo "$cwd" ; echo -n ]2\;$cwd'
alias lltod 'pwd;D="`date|cut -c5-10`";ls -la |grep "$D"'

alias lsju "ssh xenon.stanford.edu"
alias comcast "ftp djw98465@upload.comcast.net"

#alias runmysql "sudo /usr/local/mysql/bin/mysqld_safe --user=mysql &"
#alias ror "cd ~/Sites/Rails/aws/; ruby script/server"

alias ffdev='arch -arch i386 ~/Applications/Firefox.app/Contents/MacOS/firefox-bin  -no-remote -P dev -chromebug&'
