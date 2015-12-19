# hh_git_2

for branch in `git branch -r | grep -v HEAD | grep -v master `; do
   git branch --track $branch
done

git filter-branch --tag-name-filter cat --tree-filter 'rm -rf  ./frontik/testing' -- --all

git filter-branch --tag-name-filter cat --subdirectory-filter './frontik/testing/' -- --all
