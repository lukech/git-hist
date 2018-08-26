# git-utils
A collection of utility programs to help with daily coding work using git as the VCS. 

## git-hist
Making recall of git command history more smoothly (or less painful).

### Why 
With *nix build-in command history retrieval utilities, why do you need another one specific for git? 
Think about a scenario that you hope to recall a command like "git log --oneline develop..master":
1) if you type "^+R" followed by "git log", there could be a number of historical commands (including "git log" as sub-string) got match, and you'll have to go through them one-by-one (in the order of history). This could be very more painful if the git command you hope to recall was previously executed weeks or months ago. 
2) if you type "^+R" followed by "git log --oneline", by providing more exact keywords (and sequence) to safeguard a match, are you actually starting to lose the original purpose of the brain-burning salvation from history recall?

The idea of git-hist is to improve your git command recalling exprience by reaching a match with a couple of dispersive 'keywords', without needing to follow the exact sequence the command was run before). 

It is implemented by querying command history to pick the right git command to re-execute.

### Usage
````bash
$ git-hist <keyword>
````

## git-remove-obsolete-local-branches
Removing obsolete local git branches that no longer exist on remote side.

### Why 
Keeping local and remote git branches in sync could be a challenge, especially when adopting UI based feature branch merge. One typical example is working on code change in a local feature branch, and then reviewing and merging the feature branch on GitHub, which makes the local feature branch obsolete.

Instead of identifying and removing obsolete local branches manually each time, `git-remove-obsolete-local-branches` is to perform a prune fetch so that those obsolete local branches are marked `[: gone]`, and then query out all such branches, prompt user for confirmation before getting them removed.

### Usage
````bash
$ git-remove-obsolete-local-branches
The following local branches (no longer exist on the remote) will be removed:

local-legacy-br

Proceed? [Yy/Nn]y
Deleted branch local-legacy-br (was f9b0115).
````

## Supported Operating Systems
Linux & MacOS
