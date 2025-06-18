# Final Project Retrospective

## Team Members
- **Student 1:** Earl John Pulido
- **Student 2:** Dzelle Faith Tan

## 1. How did you divide the work between you and your partner?
We divided the work based on application layers to minimize overlap in the initial stages. One team member took on the "backend" logic, while the other focused on the "frontend" display logic.

-   **Partner 1 (Backend Focus):** Worked on Feature 2 (User Registration & Login) and Feature 3 (Product Management), which involved creating and managing in-memory data structures and functions in `user_controller.pseudo` and `product_model.pseudo`.
-   **Partner 2 (Frontend Focus):** Worked on Feature 4 (Storefront Display) and Feature 1 (Filter Products), which involved rendering product data and implementing filtering logic in `store_view.pseudo` and `product_controller.pseudo`.

This division allowed us to work in parallel on different files for our first set of features, making the initial merges straightforward.

## 2. What Git strategies or commands helped you most during the project?
The most helpful strategy was **feature branching**. Creating a separate branch for each feature (`feat/user-auth`, `feat/storefront-display`, etc.) was essential. It kept our `main` branch clean and stable, ensuring that incomplete or broken code never contaminated our primary codebase.

As for specific commands, the most useful were:
-   `git status`: This was our go-to command before doing anything. It provided a clear snapshot of what was modified, staged, or untracked, preventing many mistakes.
-   `git log --oneline --graph`: This was incredibly useful for visualizing how our branches diverged and, more importantly, how a merge commit brought our separate work histories back together.
-   `git pull origin main`: Running this before starting a merge was a critical habit. It ensured we were merging our feature into the most up-to-date version of the `main` branch, incorporating our partner's latest work.

## 3. Describe a merge conflict you encountered. What caused it and how did you resolve it?
We intentionally created a merge conflict as required by the project.

-   **What caused it:** The conflict occurred in the `store_view.pseudo` file. Both of us modified the exact same line—the header in the `display_products()` function—on our separate feature branches. Partner 1 merged a branch that changed the line to `"=== Our Awesome Pseudo-Shop Products ==="`. Later, Partner 2 tried to merge a branch that changed the same line to `"--- Now Showing All Available Items ---"`. When Git tried to perform the second merge, it couldn't automatically decide which version to keep.

-   **How we resolved it:**
   1.  The team member performing the merge saw the `CONFLICT` message in the terminal.
   2.  We used `git status` to confirm that `store_view.pseudo` was the file with the conflict.
   3.  We opened the file and saw the conflict markers (`<<<<<<< HEAD`, `=======`, `>>>>>>>`).
   4.  We communicated as a team and decided to create a new, combined header: `✨✨ Welcome to the All-New Pseudo-Shop! ✨✨`.
   5.  We deleted the two conflicting versions and the conflict markers, leaving only our new, agreed-upon line.
   6.  We saved the file and used `git add store_view.pseudo` to mark the conflict as resolved.
   7.  Finally, we completed the merge by running `git commit`, which finalized the merge commit.

**Lesson Learned:** Merge conflicts aren't scary if you approach them systematically. Clear communication is key to decide on a resolution.

## 4. What were the biggest challenges you faced as a team?
Our biggest challenge was coordinating the merge process and dealing with a minor technical issue. We had to be careful to communicate who was merging to `main` and when, so the other person knew to `git pull` the latest changes before starting their own merge.

We also ran into an issue where Git tried to open the `vi` editor, but the terminal environment we're using (sh-5.2$) does not have vi installed. This paused our merge unexpectedly. We learned to solve this by using `git commit -m "message"` to provide a commit message directly.

## 5. What did you learn about using Git in a collaborative setting?
Our main takeaway was that Git is as much a communication tool as it is a version control system. A well-written commit message is like a short note to your partner explaining *why* a change was made. Branch names should communicate intent and what feature is being worked on.

We also learned that a disciplined workflow (branch, code, commit, push, merge) is key to preventing chaos. You can't just save files randomly; every action has a purpose and affects the team's shared history. Trusting the process and communicating clearly saves us from major headaches in the future.

## 6. How would you improve your workflow next time?
For our next project, we would integrate two key practices from professional workflows:

1.  **Use Pull Requests (PRs):** Instead of merging locally and pushing directly to `main`, we would push our feature branches to GitHub and open a Pull Request. This would allow the other team member to review the code, add comments, and approve the changes before they are merged. This adds a crucial quality assurance step.
2.  **Use GitHub Issues:** We would create an "Issue" for each feature ticket at the start of the project. We could then link our branches and commits back to these issues (e.g., `git commit -m "feat: Implement login, fixes #2"`). This provides much better project tracking and makes it clear who is responsible for what task.

## 7. Optional: Any feedback on the activity?
The requirement to create and resolve an intentional merge conflict was extremely effective. It turned a potentially stressful event into a controlled learning experience. Facing it head-on made us much more confident about handling real conflicts in the future.

As a suggestion for improvement, providing a one-page 'cheat sheet' with the key commands for this specific workflow (git checkout -b, git pull, git push, git merge, etc.) would be a great quick reference to have during the activity. Overall, the activity was a fantastic, hands-on introduction to real-world Git collaboration.
