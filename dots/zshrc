#!/usr/bin/env bash
# If you come from bash you might have to change your $PATH.
export PATH=$HOME/bin:/usr/local/bin:$PATH
export PATH=/opt/catgenome/cli/ngb-cli/bin:$PATH
export PATH=/home/clint/pipelines/duplexseq/packages/VarDictJava/build/install/VarDict/bin:$PATH
export PATH=/usr/lib/RepeatMasker/util:$PATH}}

# Path to your oh-my-zsh installation.
export ZSH=/home/clint/.oh-my-zsh

source ~/.exports

# Set name of the theme to load. Optionally, if you set this to "random"
# it'll load a random theme each time that oh-my-zsh is loaded.
# See https://github.com/robbyrussell/oh-my-zsh/wiki/Themes
# Old: robbyrussell
ZSH_THEME="robbyrussell"

# Uncomment the following line to use case-sensitive completion.
# CASE_SENSITIVE="true"

# Uncomment the following line to use hyphen-insensitive completion. Case
# sensitive completion must be off. _ and - will be interchangeable.
# HYPHEN_INSENSITIVE="true"

# Uncomment the following line to disable bi-weekly auto-update checks.
# DISABLE_AUTO_UPDATE="true"

# Uncomment the following line to change how often to auto-update (in days).
# export UPDATE_ZSH_DAYS=13

# Uncomment the following line to disable colors in ls.
# DISABLE_LS_COLORS="true"

# Uncomment the following line to disable auto-setting terminal title.
# DISABLE_AUTO_TITLE="true"

# Uncomment the following line to enable command auto-correction.
# ENABLE_CORRECTION="true"

# Uncomment the following line to display red dots whilst waiting for completion.
COMPLETION_WAITING_DOTS="true"

# Uncomment the following line if you want to disable marking untracked files
# under VCS as dirty. This makes repository status check for large repositories
# much, much faster.
# DISABLE_UNTRACKED_FILES_DIRTY="true"

# Uncomment the following line if you want to change the command execution time
# stamp shown in the history command output.
# The optional three formats: "mm/dd/yyyy"|"dd.mm.yyyy"|"yyyy-mm-dd"
# HIST_STAMPS="mm/dd/yyyy"

# Would you like to use another custom folder than $ZSH/custom?
# ZSH_CUSTOM=/path/to/new-custom-folder

# Which plugins would you like to load? (plugins can be found in ~/.oh-my-zsh/plugins/*)
# Custom plugins may be added to ~/.oh-my-zsh/custom/plugins/
# Example format: plugins=(rails git textmate ruby lighthouse)
# Add wisely, as too many plugins slow down shell startup.
plugins=(git)

source $ZSH/oh-my-zsh.sh
source /etc/profile.d/fzf.zsh

# USER CONFIGURATION ##########################################################

EDITOR=subl3

export PS1='${ret_status} %{$fg[cyan]%}%c%{$reset_color%} $(git_prompt_info)'

# Color man pages
export LESS_TERMCAP_mb=$'\E[01;31m'
export LESS_TERMCAP_md=$'\E[01;31m'
export LESS_TERMCAP_me=$'\E[0m'
export LESS_TERMCAP_se=$'\E[0m'
export LESS_TERMCAP_so=$'\E[01;44;33m'
export LESS_TERMCAP_ue=$'\E[0m'
export LESS_TERMCAP_us=$'\E[01;32m'

# export MANPATH="/usr/local/man:$MANPATH"

# You may need to manually set your language environment
# export LANG=en_US.UTF-8

# Preferred editor for local and remote sessions
if [[ -n $SSH_CONNECTION ]]; then
  export EDITOR='vim'
else
  export EDITOR='subl3'
  export VISUAL='subl3'
fi

# Compilation flags
# export ARCHFLAGS="-arch x86_64"

# ssh
export SSH_KEY_PATH="~/.ssh/rsa_id"

# BLAST CLI
export BLASTDB=/blast/db

export PYENSEMBL_CACHE_DIR=~/scratch

# ALIASES #####################################################################

# Set personal aliases, overriding those provided by oh-my-zsh libs,
# plugins, and themes. Aliases can be placed here, though oh-my-zsh
# users are encouraged to define aliases within the ZSH_CUSTOM folder.
# For a full list of active aliases, run `alias`.
#
# Example aliases

alias zshconfig="subl3 ~/.zshrc"
alias ohmyzsh="subl3 ~/.oh-my-zsh"

alias cd..='cd ..'
alias cp='cp -i'
alias d='ls'
alias df='df -h -x supermount'
alias du='du -h'
alias egrep='egrep --color'
alias fgrep='fgrep --color'
alias grep='grep --color'

alias ls='ls -lhF --color=auto'
alias l='ls -lhF --color=auto '
alias la='ls -lhFa --color=auto'
alias lt='ls -lhFt --color=auto'
alias ld='ls -lhFd */ --color=auto'
alias lta='ls -lhFta --color=auto'
alias ltd='ls -lhFtd --color=auto'

alias md='mkdir'
alias mv='mv -i'
alias p='cd -'
alias rd='rmdir'
alias rm='rm -i'

alias less='less -SF -# 15'

alias .=source

alias igv='igv > /dev/null 2>&1 &'
alias xclip='xclip -selection c'
alias lollipops='/home/clint/go/bin/lollipops'

alias cls=clear
alias w3m='w3m -o ext_image_viewer=0'

# BINDKEYS ####################################################################

# bindkey '^[[6~  page down
# bindkey '^[[2~  insert

bindkey '^[[5~' beginning-of-history
bindkey '^[[H'  beginning-of-line
bindkey '^[[3~' delete-char
bindkey '\e[8'  end-of-line

# mappings for making up and down arrow searching through history:
bindkey '\e[A' history-search-backward
bindkey '\e[B' history-search-forward
bindkey '\e[C' forward-char
bindkey '\e[D' backward-char

#Use [Tab] and [Shift]+[Tab] to cycle through all the possible completions:
bindkey '\t'  menu-complete
bindkey '\e[Z' menu-complete-backward

# HISTORY #####################################################################

export HISTFILESIZE=20000
export HISTSIZE=10000

# Combine multiline commands into one in history
# Ignore duplicates, ls without options and builtin commands
HISTCONTROL=ignoredups
export HISTIGNORE="&:ls:[bf]g:exit"

# FUNCTIONS ###################################################################

# Sudo the last command if failed otherwise sudo
s() { # do sudo, or sudo the last command if no argument given
    if [[ $# == 0 ]]; then
        sudo $(history -p '!!')
    else
        sudo "$@"
    fi
}


# Print the relative working directory
relwd () {
    echo "${PWD/#$HOME/~}"
}


# Get complement of uppercase DNA
comp() {
    echo $1 | tr ATCG TAGC
}

# Get reverse complement of uppercase DNA
revcomp() {
    echo $1 | rev | tr ATCGatcg TAGCtagc
}

# display a list of supported colors
# From https://github.com/jleclanche/dotfiles
function lscolors {
    ((cols = $COLUMNS - 4))
    s=$(printf %${cols}s)
    for i in {000..$(tput colors)}; do
        echo -e $i $(tput setaf $i; tput setab $i)${s// /=}$(tput op);
    done
}

# Display a table of sequencers and associated costs
function sequencing-cost {
    curl "https://docs.google.com/spreadsheets/d/1GMMfhyLK0-q8XkIo3YxlWaZA5vVMuhU1kg41g4xLkXc/export?gid=4&format=csv" \
        | grep -v '^#' \
        | grep -v '^"' \
        | column -t -s\, \
        | less -S
}

# get the content type of an http resource
# From https://github.com/jleclanche/dotfiles
function htmime {
    if [[ -z $1 ]]; then
        print "USAGE: htmime <URL>"
        return 1
    fi
    mime=$(curl -sIX HEAD $1 | sed -nr "s/Content-Type: (.+)/\1/p")
    print $mime
}

# urlencode text
# From https://github.com/jleclanche/dotfiles
function urlencode {
    print "${${(j: :)@}//(#b)(?)/%$[[##16]##${match[1]}]}"
}

# open a web browser on google for a query
# From https://github.com/jleclanche/dotfiles
function google {
    xdg-open "https://www.google.com/search?q=`urlencode "${(j: :)@}"`"
}

# print a separator banner, as wide as the terminal
# From https://github.com/jleclanche/dotfiles
function hr {
    print ${(l:COLUMNS::=:)}
}

# get public ip
# From https://github.com/jleclanche/dotfiles
function myip {
    local api
    case "$1" in
        "-4")
            api="http://v4.ipv6-test.com/api/myip.php"
            ;;
        "-6")
            api="http://v6.ipv6-test.com/api/myip.php"
            ;;
        *)
            api="http://ipv6-test.com/api/myip.php"
            ;;
    esac
    curl -s "$api"
    echo # Newline.
}

# Create short urls via http://goo.gl using curl(1).
# Contributed back to grml zshrc
# API reference: https://code.google.com/apis/urlshortener/
# From https://github.com/jleclanche/dotfiles
function zurl {
    if [[ -z $1 ]]; then
        print "USAGE: $0 <URL>"
        return 1
    fi

    local url=$1
    local api="https://www.googleapis.com/urlshortener/v1/url"
    local data

    # Prepend "http://" to given URL where necessary for later output.
    if [[ $url != http(s|)://* ]]; then
        url="http://$url"
    fi
    local json="{\"longUrl\": \"$url\"}"

    data=$(curl --silent -H "Content-Type: application/json" -d $json $api)
    # Match against a regex and print it
    if [[ $data =~ '"id": "(http://goo.gl/[[:alnum:]]+)"' ]]; then
        print $match
    fi
}

# Opens the file using Gnome
function open {
    xdg-open ${@} > /dev/null 2>&1 &
}

function compute {
    bc -l <<< ${@}
}

function tsv {
    column -t -s $'\t' ${1} | less -JQi -# 15
}

function csv {
    column -t -s $',' ${1} | less -JQi -# 15
}


function asciicast2gif {
    sudo docker run --rm -v $PWD:/data asciinema/asciicast2gif
}


function fstabalign {
    # usage: fstabalign [FILE]

    # This script will output fstab or other file as column aligned.
    # It will not alter blank lines or #hash comments.

    if [ -z "$1" ]; then
        FILE=$(cat /etc/fstab)
    else
        FILE=$(cat "$1")
    fi

    # Separate the file contents into aligned and unaligned parts.
    OUT_ALIGNED=$(echo "$FILE" | sed 's/^\s*#.*//' | nl -ba | column -t)
    OUT_UNALIGNED=$(echo "$FILE" | sed 's/^\s*[^#].*//' $src | nl -ba)

    # Remerge aligned and unaligned parts.
    while read; do
        line_aligned="$REPLY"
        read -u 3; line_unaligned="$REPLY"
        line_aligned=$(  echo "$line_aligned"   | sed 's/\s*[0-9]*\s*//')
        line_unaligned=$(echo "$line_unaligned" | sed 's/\s*[0-9]*\s*//')
        echo "$line_aligned$line_unaligned"
    done < <(echo "$OUT_ALIGNED") 3< <(echo "$OUT_UNALIGNED")
}

function random-string {
    if [ $# -eq 0 ]; then
        length=32
    else
        length="${1}"
    fi

    cat /dev/urandom | tr -dc 'a-zA-Z0-9' | fold -w "${length}" | head -n 1
}

function nyancat {
    telnet nyancat.dakko.us
}


function get-permissions {
    find   \( -type f -a \( \( ! -group root -o ! -user root \) -o \( ! -perm 755 -a ! -perm 644 \) \) \) \
        -o \( -type d -a \( ! -group root -o ! -user root -o ! -perm 755 \) \) \
        | while read line; do stat -c "%u %g %a %n" $line ; done

}

function set-default-file-dir-permissions {
    find -type d | while read dirs; do chmod 755 "$dirs"; done
    find -type f | while read files; do chmod 644 "$files"; done
}

# BAM #########################################################################

function sample-names-description-from-bam {
    samtools view -H ${1} | grep "@RG" | sed -r 's/.*?(SM:\S*).*?(DS:[^\t]*)/\1\t\2/'
}


# BED #########################################################################

function bedTotalLength {

    if read -t 0; then
        awk '{SUM += $3-$2} END {print SUM}'
    else
        awk '{SUM += $3-$2} END {print SUM}' < "${1}"
    fi
}

# AWS #########################################################################

function submit {
    local config=${1}
    shift
    aws s3 cp ${config} s3://twinstrand-queue/to-aws/ ${@}
}

# SAY HELLO TO ME #############################################################

#/usr/bin/screenfetch; echo

# Only load Liquid Prompt in interactive shells, not from a script or from scp
#[[ $- = *i* ]] && source ~/repos/liquidprompt/liquidprompt


autoload -U promptinit; promptinit
prompt pure
