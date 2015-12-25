# hh_git_2

//Если нужны все ветки,а не только мастер, можно использовать баш.

//к filter-branch в этом случае будет необходимо добавить --all

for branch in `git branch -r | grep -v HEAD | grep -v master `; do
   git branch --track $branch
done

git clone https://github.com/hhru/frontik.git


//Команда в репозитории, где будет только папка testing

git filter-branch --tag-name-filter cat --subdirectory-filter './frontik/testing/' --prune-empty -- --all

//Команда в репозитории, где будет все остальное

git filter-branch --tag-name-filter cat --tree-filter 'rm -rf  ./frontik/testing' --prune-empty -- --all

git remote rm origin

git remote add origin https://github.com/Kapiton42/FrontikInclTesting.git//FrontikNotIncludeTesting для всего остального

git push -u origin master
