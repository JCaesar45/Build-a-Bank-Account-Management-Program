````markdown
# Bank Account Management Program

This is a simple JavaScript project that simulates a basic bank account system. It allows users to deposit and withdraw money, track transactions, and check their account balance.

## Features

- Create a bank account with an initial balance of $0
- Deposit funds with validation
- Withdraw funds with balance and input validation
- View the current balance
- List all deposits
- List all withdrawals
- Stores transactions as objects with `type` and `amount`

## User Stories

- ✅ I want to create a bank account with an initial balance of $0
- ✅ I want to deposit money and see the new balance
- ✅ I want to withdraw money if I have sufficient funds
- ✅ I want to see a list of all my deposits
- ✅ I want to see a list of all my withdrawals
- ✅ I want to see my current balance

## Code Structure

```javascript
class BankAccount {
  constructor() {
    this.balance = 0;
    this.transactions = [];
  }

  deposit(amount) {
    if (amount > 0) {
      this.transactions.push({ type: 'deposit', amount });
      this.balance += amount;
      return `Successfully deposited $${amount}. New balance: $${this.balance}`;
    }
    return "Deposit amount must be greater than zero.";
  }

  withdraw(amount) {
    if (amount > 0 && amount <= this.balance) {
      this.transactions.push({ type: 'withdraw', amount });
      this.balance -= amount;
      return `Successfully withdrew $${amount}. New balance: $${this.balance}`;
    }
    return "Insufficient balance or invalid amount.";
  }

  checkBalance() {
    return `Current balance: $${this.balance}`;
  }

  listAllDeposits() {
    const deposits = this.transactions
      .filter(tx => tx.type === 'deposit')
      .map(tx => tx.amount);
    return `Deposits: ${deposits.join(',')}`;
  }

  listAllWithdrawals() {
    const withdrawals = this.transactions
      .filter(tx => tx.type === 'withdraw')
      .map(tx => tx.amount);
    return `Withdrawals: ${withdrawals.join(',')}`;
  }
}
```

## Example Usage

```javascript
const myAccount = new BankAccount();

myAccount.deposit(150);     // "Successfully deposited $150. New balance: $150"
myAccount.deposit(75);      // "Successfully deposited $75. New balance: $225"
myAccount.withdraw(50);     // "Successfully withdrew $50. New balance: $175"
myAccount.withdraw(30);     // "Successfully withdrew $30. New balance: $145"
myAccount.deposit(20);      // "Successfully deposited $20. New balance: $165"

myAccount.checkBalance();         // "Current balance: $165"
myAccount.listAllDeposits();      // "Deposits: 150,75,20"
myAccount.listAllWithdrawals();   // "Withdrawals: 50,30"
```

## Requirements

* JavaScript (ES6+)
* Node.js or any JavaScript runtime to execute the script

## License

This project is open-source and free to use.

```

You can name this file `README.md` and place it in your project folder. Let me know if you'd like to add testing instructions or publish it on GitHub.
```
