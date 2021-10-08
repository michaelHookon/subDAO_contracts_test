# Vote Module

## Interface

### new() -> Self

Init a new vote module.

### new_vote(title: String, desc: String, vote_time: u64, support_require_num: u64, min_require_num: u64, choices: String) -> u64

Create a new vote without trigger.

params:

* title: the vote's title
* desc: the vote's desc
* vote_time: how long the vote durate by milliseconds.
* support_require_num: minimum support require numbers.
* min_require_num: minimum voter require numbers.
* choices: all vote choice, split by `|` , eg: A|B|C|D 

return

* vote_id

### new_vote_with_transfer(title: String, desc: String, vote_time: u64, support_require_num: u64, min_require_num: u64, choices: String, erc20_address:AccountId, to_address:AccountId, value:u64) -> u64

create a new vote with transfer trigger.

* title: the vote's title
* desc: the vote's desc
* vote_time: how long the vote durate by milliseconds.
* support_require_num: minimum support require numbers.
* min_require_num: minimum voter require numbers.
* choices: all vote choice, split by `|` , eg: A|B|C|D
* erc20_address: a address of a erc20 contract.
* to_address: when trigger invoke, who will receive tokens.
* value: tokens amount.

return

* vote_id


### vote(vote_id: VoteId, support_choice: u32, voter: AccountId) -> bool

Do a vote.

params:

* vote_id: a vote id, u64
* support_choice: which choice_id to be choosed, from zero. so, if there is four choices like A, B, C, D. Here 0 refers A, 1 refers B etc.
* voter: the voter account id

return:

* result: true/false

### execute(vote_id: VoteId)

execute a vote. 

mark status to executed.

### query_voter_vote_one(vote_id: VoteId, voter: AccountId) -> bool

query a voter has voted one vote.

### query_one_vote(vote_id: VoteId) -> DisplayVote

query vote by vote_id

if vote_id didn't exist, the function will runtime overhead.

### query_all_vote() -> alloc::vec::Vec<DisplayVote>

query all votes

### query_history_vote() -> alloc::vec::Vec<DisplayVote>

query history votes.

### query_active_vote() -> alloc::vec::Vec<DisplayVote>

query all active votes.

### query_pending_vote() -> alloc::vec::Vec<DisplayVote>

query all finished but unexecuted votes.