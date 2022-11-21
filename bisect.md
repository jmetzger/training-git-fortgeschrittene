# git bisect 

## Walkthrough 

```
# Step 1: experimental repo
mkdir git_bisect_tests
cd git_bisect_tests
git init
```

```
# Step 2: Fill with experimental data 
echo row > test.txt
git add -A && git commit -m "Adding first row"
echo row >> test.txt
git add -A && git commit -m "Adding second row"
echo row >> test.txt
git add -A && git commit -m "Adding third row"
echo your >> test.txt
git add -A && git commit -m "Adding the word 'your'"
echo boat >> test.txt
git add -A && git commit -m "Adding the word 'boat'"
echo gently >> test.txt
git add -A && git commit -m "Adding the word 'gently'"
sed -i -e 's/boat/car/g' test.txt 
git add -A && git commit -m "Changing the word 'boat' to 'car'"
echo down >> test.txt
git add -A && git commit -m "Adding the word 'down'"
echo the >> test.txt
git add -A && git commit -m "Adding the word 'the'"
echo stream >> test.txt
git add -A && git commit -m "Adding the word 'stream'"
```

```
# Step 3: find bug
# 'boat' was overwritten by 'car' INCIDENTALLY
cat test.txt
```





## Reference 

  * https://www.metaltoad.com/blog/beginners-guide-git-bisect-process-elimination
