# Cafe grader UVa bot

These are scripts for [Cafe Grader](https://github.com/cafe-grader-team)
that make [UVa Online Judge](https://uva.onlinejudge.org/) submissions.

## How to use it

In short, put config in `judge/uva.yml`.  For the problem you want to
grade using UVa grader, name it in this format `uva{PROBLEM-ID}_{anythingyoulike}`
(so that the script can find the UVa problem id), and put `scripts/judge` of this project
in `{cafe-grader-home}/judge/ev/[problem_name]/script`.
The judge script will submit the submissions to UVa grader using its web interface.

To synchronize the score, put `scripts/sync` in
`{cafe-grader-home}/judge/scripts` and call it from time to time.  The
`sync` script uses [uHunt](http://uhunt.felix-halim.net/api)'s api by
Felix Halim.

## Requirements

Ruby [Mechanize](https://github.com/sparklemotion/mechanize) gem.  Install it with:

    gem install mechanize

## Config

Create `{cafe-grader-home}/judge/uva.yml` and put your info as shown below.

    username: YOUR-UVA-USERNAME
    password: YOUR-UVA-PASSWORD
    online_judge_id: YOUR-ONLINE-JUDGE-ID

The online judge ID can be found in My Account page in the UVa website.

## Problem dir config

In judge's ev dir (usually in `{cafe-grader-home}/judge/ev`), create a directory for the problem.  Inside it create two subdirectories: `script` and `test_cases`.  Copy, or preferably link, `scripts/judge` to `{problem-name}/script/judge` so that the grader calls it.

For example, if your problem name is `uva100_3nplus1`, the directory should look like:

    - ev/uva100_3nplus1
      - ev/uva100_3nplus1/script
        - ev/uva100_3nplus1/script/judge
      - ev/uva100_3nplus1/test_cases
