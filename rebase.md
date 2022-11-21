# git rebase examples 

## Example 1: We are on the branch we want to rebase

```
# Step 1: Change something in feature/4721
git checkout -b feature/4721
echo "hello" > foo 
git add . 
git commit -am "foo" 

# Step 2: change something in master 
git checkout master
echo "my master" > foo 
git add .
git commit -am "foo in master"

# Step 3: Changing back to feature 
git checkout -b feature/4721
# We want to rebase our work based on master
# So: 1) rewind on master
#     2) replay changes of feature on top 
git rebase master 
# Now we should have conflict 

```

