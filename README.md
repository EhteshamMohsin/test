jq: error: $repo is not defined at <top-level>, line 1:
.[] | "\($repo),\(.login),\(.permissions | to_entries[] | select(.value == true) | .key)"         
jq: 1 compile error
Processing repository: pbi
jq: error: $repo is not defined at <top-level>, line 1:
.[] | "\($repo),\(.login),\(.permissions | to_entries[] | select(.value == true) | .key)"         
jq: 1 compile error
Processing repository: somatils
