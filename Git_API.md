<pre>
<code>
#!/bin/bash

# 변수 설정
GITHUB_TOKEN="YOUR_ACCESS_TOKEN"
REPO_OWNER="username"
REPO_NAME="repository"
BASE_BRANCH="main"
MODIFY_FILE_PATH="path/to/file.txt"
MODIFY_STRING="new content"
GIT_EMAIL="your-email@example.com"
GIT_NAME="Your Name"

# 1. Clone the repository
git clone https://github.com/${REPO_OWNER}/${REPO_NAME}.git
cd ${REPO_NAME}

# 2. Create a 5-digit hash for the new branch name
HASH=$(openssl rand -hex 3 | cut -c1-5)  # Generate a 5-digit hex hash
BRANCH_NAME="update-${HASH}"

# 3. Create a new branch and switch to it
git checkout -b ${BRANCH_NAME}

# 4. Modify the code
echo "${MODIFY_STRING}" > ${MODIFY_FILE_PATH}

# 5. Commit and push the changes
git config user.email "${GIT_EMAIL}"
git config user.name "${GIT_NAME}"
git add ${MODIFY_FILE_PATH}
git commit -m "Automated update with hash ${HASH}"
git push origin ${BRANCH_NAME}

# 6. Create a Pull Request
PR_RESPONSE=$(curl -X POST -H "Authorization: token ${GITHUB_TOKEN}" \
  -H "Accept: application/vnd.github.v3+json" \
  -d "{\"title\":\"Automated PR with hash ${HASH}\",\"body\":\"This PR was created and merged automatically.\",\"head\":\"${BRANCH_NAME}\",\"base\":\"${BASE_BRANCH}\"}" \
  https://api.github.com/repos/${REPO_OWNER}/${REPO_NAME}/pulls)

# Extract the Pull Request number from the response
PR_NUMBER=$(echo ${PR_RESPONSE} | jq .number)

# 7. Add a review to the Pull Request
curl -X POST -H "Authorization: token ${GITHUB_TOKEN}" \
  -H "Accept: application/vnd.github.v3+json" \
  -d "{\"body\":\"Looks good to me!\",\"event\":\"APPROVE\"}" \
  https://api.github.com/repos/${REPO_OWNER}/${REPO_NAME}/pulls/${PR_NUMBER}/reviews

# 8. Merge the Pull Request
curl -X PATCH -H "Authorization: token ${GITHUB_TOKEN}" \
  -H "Accept: application/vnd.github.v3+json" \
  -d '{"commit_title":"Automated merge with hash '${HASH}'","commit_message":"Merging changes automatically","merge_method":"merge"}' \
  https://api.github.com/repos/${REPO_OWNER}/${REPO_NAME}/pulls/${PR_NUMBER}/merge

echo "Pull Request #${PR_NUMBER} has been created, reviewed, and merged successfully."
</code>
</pre>
