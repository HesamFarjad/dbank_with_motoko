
Interactive Motoko-based DFX project with Candid UI integration


1. Running `dfx new dbank`**

This command initializes a new Internet Computer project named `dbank`. The DFX tool sets up the project structure and creates essential files like `main.mo`, `dfx.json`, `README.md`, and frontend files such as `index.js`, `index.html`, and `logo.png`.

✅ This is the starting point of my Internet Computer application.

---

2. Welcome Message from DFX

After running `dfx new`, you see a welcome banner with links to helpful documentation including the Quick Start, SDK Developer Guide, and the Motoko Language Reference.

---

3. Starting the Local Network with dfx start

Running `dfx start` and accessing the local network**

This command launches the local Internet Computer replica. The output shows the system is running at `http://127.0.0.1:8000/`.

---

4. Deploying the Project with dfx deploy

Running `dfx deploy` to install the canister**

Here, `dfx deploy` builds and installs our canisters locally. The output shows the canisters were created and the frontend was built.

✅ This step is required to make your backend code available for testing.

---

5. Getting the Candid UI Canister ID

Retrieving the Candid UI Canister ID**

The command `dfx canister id __Candid_UI` returns the ID of the built-in Candid interface. we'll use this ID to access the graphical UI in your browser.

📎 we’ll need this ID to launch the Candid interface.

---

6. Candid UI URL Format

Browser URL to access the Candid UI**

To open the Candid interface, use this URL format:
http://127.0.0.1:8000/?canisterId=<CANDID-UI-CANISTER-ID>

🌐 This web UI allows us to interact with our canisters visually instead of using terminal commands.

---

7. Pasting the Canister ID into the UI

![Screenshot 2025-06-22 at 20 48 26](https://github.com/user-attachments/assets/e339c85d-e0f9-4397-bcf5-bc08fa9e5984)


Entering your project’s canister ID into Candid UI**

By entering your canister ID, the Candid UI will load all public functions defined in your Motoko code such as `topUp` and `withdraw`.

🎛 Now we can call our canister's functions using the UI.

---

## 🔄 ⏳ How sync and async execution differ on the Internet Computer

![Screenshot 2025-06-22 at 20 52 52](https://github.com/user-attachments/assets/ec5557db-e08c-405f-a3ba-c5daf4f6104b)

This change also reflects the distinction between asynchronous and synchronous behavior in Motoko:

- The checkBalance() function is defined as public query func and is asynchronous. Since it's a query, it’s non-mutating, fast, and doesn’t require consensus. The use of async indicates that the result is returned in the future.

- The withdraw(amount: Nat) function is a regular public func, making it synchronous. It performs state mutation (deducting from the balance), so it requires an update call that waits for execution and consensus.


## 🧠 Orthogonal Persistence in Motoko with `stable var`

The diagram below illustrates how orthogonal persistence works in the Internet Computer using the `stable` keyword in Motoko.

- `var` is a regular in-memory variable. It **resets** when you upgrade the canister.
- `stable var` is a persistent variable. It **retains its value** even after upgrades.

<img width="1150" alt="Screenshot 2025-06-22 at 13 21 25" src="https://github.com/user-attachments/assets/1e6d8b6f-58f4-4ff9-b235-660b73005a8c" />



### 💡 Compound Interest Logic

The implementation of a `compound()` function in Motoko, which simulates compound interest over time.

It uses `Time.now()` to calculate the time elapsed since the last update, and applies a growth formula:  

<img width="1238" alt="Screenshot 2025-06-22 at 18 56 35" src="https://github.com/user-attachments/assets/e66fdbf9-d4d7-49cc-95ac-3e530677b5fe" />


The adjacent diagrams help visualize the concept of reinvestment and the mathematical formula for compound interest.  
Albert Einstein is famously quoted as calling compound interest “the most powerful force in the universe.”




## 🌐🌐 Get help for working with the Internet Computer 🌐🌐

[Official Developer Docs](https://internetcomputer.org/)

[Official Dfinity Forum](https://forum.dfinity.org/)


