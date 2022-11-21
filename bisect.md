# git bisect 

## What for ?

  * My developers are working on a project 
  * One developer creates a bug 
  * That's within hundreds of commits 
  * bisect helps to find, where it was introduced

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

```
# Step 4.1: Find good commit -> "boat"
git log 
```

```
# Step 4.2: Find bad commit -> "latest" -> HEAD 
```

```
# Step 4.3: start the process:
# Start: git bisect start
# Done: git bisect reset 
git bisect start 

```

```
# Step 5: enter the good commit
git bisect good <commit-from-boat>
```

```
# Step 6: enter the bad commit
# last commit was bad 
git bisect bad HEAD
```

```
# Step 7.1: Git checks out a version in between
cat test.txt 
# is it good or bad ? (holds the word car or not) 
git bisect bad 
```

```
# Step 7.2: git again checks out a version in between
cat test.txt
# Good or bad ? (holds the word "boat" -> good , "car" -> bad 
git bisect good
# now git shows us the first bad commit 
```

```
# Step 8: End the bisect wizard 
git bisect reset 
```



## Reference 

  * https://www.metaltoad.com/blog/beginners-guide-git-bisect-process-elimination
