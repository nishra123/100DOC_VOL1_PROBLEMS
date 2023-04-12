Given a string path, which is an absolute path (starting with a slash '/') to a file or directory in a Unix-style file system, convert it to the simplified canonical path.

In a Unix-style file system, a period '.' refers to the current directory, a double period '..' refers to the directory up a level, and any multiple consecutive slashes (i.e. '//') are treated as a single slash '/'. For this problem, any other format of periods such as '...' are treated as file/directory names.

The canonical path should have the following format:

The path starts with a single slash '/'.
Any two directories are separated by a single slash '/'.
The path does not end with a trailing '/'.
The path only contains the directories on the path from the root directory to the target file or directory (i.e., no period '.' or double period '..')
Return the simplified canonical path.

 

Example 1:

Input: path = "/home/"
Output: "/home"
Explanation: Note that there is no trailing slash after the last directory name.
Example 2:

Input: path = "/../"
Output: "/"
Explanation: Going one level up from the root directory is a no-op, as the root level is the highest level you can go.
Example 3:

Input: path = "/home//foo/"
Output: "/home/foo"
Explanation: In the canonical path, multiple consecutive slashes are replaced by a single one.
 

Constraints:

1 <= path.length <= 3000
path consists of English letters, digits, period '.', slash '/' or '_'.
path is a valid absolute Unix path.

```cpp
string simplifyPath(string path) {
    vector<string> tokens;  // create a vector to store directory names
    stringstream ss(path);  // create a stringstream object to split the path string
    string token;  // create a string variable to hold each directory name
    while (getline(ss, token, '/')) {  // iterate through each token in the stringstream
        if (token == "" || token == ".") continue;  // ignore empty or '.' tokens
        if (token == ".." && !tokens.empty()) {  // if token is '..', remove the previous directory from vector
            tokens.pop_back();
        } else if (token != "..") {  // if token is not '..', add it to vector
            tokens.push_back(token);
        }
    }
    if (tokens.empty()) return "/";  // if vector is empty, return root directory
    string canonicalPath;  // create a string to hold the simplified canonical path
    for (const auto& token : tokens) {  // iterate through each directory name in the vector
        canonicalPath += "/" + token;  // add the directory name to the canonical path string
    }
    return canonicalPath;  // return the simplified canonical path
}
```
