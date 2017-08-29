# Amend author of specific commit

If you want to amend the author of a specific commit in git history, you can use the following command:

## Git Command

```
git commit --amend --author="Author Name <email@address.com>"
```

## Example

This is a part of my commit history :
```
commit b51520ad4d8e38f7ebd68a5261b2b2d8af68c773
Author: binggre <wowzzangga@gmail.com>
Date:   Fri Aug 25 14:38:33 2017 +1000

    Translate multer options

commit bbeb518dcef3dba78b400fbc5806cb168bf04fe3
Author: jiyun sung <binggre@192-168-1-117.tpgi.com.au>
Date:   Thu Aug 24 16:21:58 2017 +1000

    Translate options article in Readme file.

commit fdb813bdcfe05a3d2540c3eb855f365b97d98941
Author: jiyun sung <binggre@jiyuns-MacBook-Pro.local>
Date:   Thu Aug 24 14:10:08 2017 +1000

    initial translation in Korean.

commit 7ef2e81215e9b773204df44fb4aee29e58340061
Author: Linus Unnebäck <linus@folkdatorn.se>
Date:   Wed Jan 25 19:21:43 2017 +0100

    version: 1.3.0
```

I want to change the author of 2 commits which are `fdb813b` and `bbeb518` to `binggre <wowzzangga@gmail.com>`

## How to amend

1. ``` git rebase -i 7ef2e ```

2. Now you can see like this:

```
pick fdb813b initial translation in Korean.
pick bbeb518 Translate options article in Readme file.
pick b51520a Translate multer options
pick 9096ab3 translate memory storage article in Korean
pick 7dfe1e6 Translate filFilter option article in Korean
pick 8365a07 Translate remaining articles in Korean
pick 131f75b Polish translation
pick 924a3c0 Translate comment blocks in example codes in Korean

# Rebase fdb813b..924a3c0 onto fdb813b (8 commands)
```

3. Change `pick` to `edit` for both `fdb813b` and `bbeb518`

4. Once the rebase started, it would first pause at `fdb813b`

5. Then run this command: 
```git commit --amend --author="binggre <wowzzangga@gmail.com>"```

6. ``` git rebase --continue ```

7. It would pause again at `bbeb518`

8. Repeat ```5``` and ```6```

9. Once the rebase complete, ``` git push -f ``` . This will push your changes by force.

## Reference

[StackOverflow](https://stackoverflow.com/questions/3042437/change-commit-author-at-one-specific-commit)