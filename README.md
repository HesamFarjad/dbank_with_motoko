
Interactive Motoko-based DFX project with Candid UI integration


![1](https://github.com/user-attachments/assets/534c3f2d-0c2f-4f8d-b55e-058ad5ee86c4)

: Running `dfx new dbank`**

This command initializes a new Internet Computer project named `dbank`. The DFX tool sets up the project structure and creates essential files like `main.mo`, `dfx.json`, `README.md`, and frontend files such as `index.js`, `index.html`, and `logo.png`.

✅ This is the starting point of my Internet Computer application.

---

🖼️ 2. Welcome Message from DFX

![2](https://github.com/user-attachments/assets/457b16b4-8db2-43c4-851e-cdd591ceb788)

: Welcome banner after project creation**

After running `dfx new`, you see a welcome banner with links to helpful documentation including the Quick Start, SDK Developer Guide, and the Motoko Language Reference.

💡 Tip: These links are great for getting familiar with the Internet Computer environment.

---

🖼️ 3. Starting the Local Network with dfx start

![3](https://github.com/user-attachments/assets/a77ba51d-8f67-4329-9ac2-75c15fd038b6)

: Running `dfx start` and accessing the local network**

This command launches the local Internet Computer replica. The output shows the system is running at `http://127.0.0.1:8000/`.

🔧 On the right side, you can see the initial code in the `main.mo` file.

---

🖼️ 4. Deploying the Project with dfx deploy

<img width="779" alt="4" src="https://github.com/user-attachments/assets/2ce0410b-8409-49d4-9a30-7598d6db4703" />

: Running `dfx deploy` to install the canister**

Here, `dfx deploy` builds and installs our canisters locally. The output shows the canisters were created and the frontend was built.

✅ This step is required to make your backend code available for testing.

---

🖼️ 5. Getting the Candid UI Canister ID

<img width="778" alt="5" src="https://github.com/user-attachments/assets/cdba2ded-9b8b-4ed6-9879-6e962ae54468" />

: Retrieving the Candid UI Canister ID**

The command `dfx canister id __Candid_UI` returns the ID of the built-in Candid interface. we'll use this ID to access the graphical UI in your browser.

📎 we’ll need this ID to launch the Candid interface.

---

🖼️ 6. Candid UI URL Format

![6](https://github.com/user-attachments/assets/c8f95fd7-d4e1-4acc-a06d-eb35707232b6)

: Browser URL to access the Candid UI**

To open the Candid interface, use this URL format:
http://127.0.0.1:8000/?canisterId=<CANDID-UI-CANISTER-ID>

🌐 This web UI allows us to interact with our canisters visually instead of using terminal commands.

---

🖼️ 7. Default Candid UI Before Connecting

<img width="1439" alt="7" src="https://github.com/user-attachments/assets/d58074df-f839-4c6e-bfa5-4d758b6e0fd6" />

: Default Candid UI screen**

This is what the Candid UI looks like before connecting to a specific canister. You can manually input a canister ID or upload a `.did` file.

🎯 Useful for exploring canister interfaces.

---

🖼️ 8. Getting Your Project’s Canister ID

<img width="792" alt="8" src="https://github.com/user-attachments/assets/1f51ff33-7582-4bc7-b7a2-668f402a88d0" />

: Getting the `dbank` canister ID**

Using the command:
dfx canister id dbank

we can retrieve the ID for your own canister. This ID is required for interaction in Candid UI.

---

🖼️ 9. Pasting the Canister ID into the UI

<img width="898" alt="9" src="https://github.com/user-attachments/assets/b027466f-489c-4427-9e73-3384c504c280" />

: Entering your project’s canister ID into Candid UI**

By entering your canister ID, the Candid UI will load all public functions defined in your Motoko code such as `topUp` and `withdraw`.

🎛 Now we can call our canister's functions using the UI.

---

🖼️ 10. Interacting with Canister Functions in Candid UI

![10](https://github.com/user-attachments/assets/ad942813-cbab-4e72-a452-a1bec07c4331)

: Full Candid UI with `topUp` and `withdraw` methods**

This view displays your canister’s public functions and allows you to enter arguments and execute them. You can see the result in the output log.

✅ No need to use `dfx canister call ...` manually in terminal anymore — it’s all done visually!



## 🔄 ⏳ How sync and async execution differ on the Internet Computer

![Screenshot 2025-06-22 at 11 55 53](https://github.com/user-attachments/assets/6de4a966-d052-4d72-b121-bc8f03972865)

This change also reflects the distinction between asynchronous and synchronous behavior in Motoko:

- The checkBalance() function is defined as public query func and is asynchronous. Since it's a query, it’s non-mutating, fast, and doesn’t require consensus. The use of async indicates that the result is returned in the future.

- The withdraw(amount: Nat) function is a regular public func, making it synchronous. It performs state mutation (deducting from the balance), so it requires an update call that waits for execution and consensus.


## 🧠 Orthogonal Persistence in Motoko with `stable var`

The diagram below illustrates how orthogonal persistence works in the Internet Computer using the `stable` keyword in Motoko.

- `var` is a regular in-memory variable. It **resets** when you upgrade the canister.
- `stable var` is a persistent variable. It **retains its value** even after upgrades.

<img width="1150" alt="Screenshot 2025-06-22 at 13 21 25" src="https://github.com/user-attachments/assets/10a92a76-af07-4343-a27f-10bff53baf82" />


### 💡 Compound Interest Logic

The implementation of a `compound()` function in Motoko, which simulates compound interest over time.

It uses `Time.now()` to calculate the time elapsed since the last update, and applies a growth formula:  
<img width="1238" alt="Screenshot 2025-06-22 at 18 56 35" src="https://github.com/user-attachments/assets/bc332103-d61d-4fd4-a3fd-40b1e15e582f" />

The adjacent diagrams help visualize the concept of reinvestment and the mathematical formula for compound interest.  
Albert Einstein is famously quoted as calling compound interest “the most powerful force in the universe.”
