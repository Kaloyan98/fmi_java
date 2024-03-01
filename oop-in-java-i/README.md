Object-Oriented Programming with Java (Part I)
Virtual Wallet Application 💳

We are creating an application for managing virtual cards. Our virtual wallet will have the following basic functionalities:

Creating a new card
Loading a specific card with money
Making a payment with a specific card
Retrieving a specific card by name
👉 The virtual wallet can store up to 5 cards.

Virtual Wallet Interface

For this purpose, let's have an interface VirtualWalletAPI:

-->
package bg.sofia.uni.fmi.mjt.virtualwallet.core;

public interface VirtualWalletAPI {

    boolean registerCard(Card card);

    boolean executePayment(Card card, PaymentInfo paymentInfo);

    boolean feed(Card card, double amount);

    Card getCardByName(String name);

    int getTotalNumberOfCards();
}
<--


Create a concrete class named VirtualWallet that implements this interface:

-->
package bg.sofia.uni.fmi.mjt.virtualwallet.core;

public class VirtualWallet implements VirtualWalletAPI {

    public VirtualWallet() {
        // constructor implementation
    }

    // implement interface methods here
}
<--


Cards

👉 VirtualWallet will support two types of cards - StandardCard and GoldenCard.

👉 When paying with a GoldenCard, we get a 15% cashback on the purchase.

The StandardCard and GoldenCard classes should inherit from the abstract class Card:

-->
package bg.sofia.uni.fmi.mjt.virtualwallet.core.card;

public abstract class Card {

    public Card(String name) {
        // constructor implementation
    }

    public abstract boolean executePayment(double cost);

    public String getName() {
        // method implementation
    }

    public double getAmount() {
        // method implementation
    }
}
<--


The difference in behavior between StandardCard and GoldenCard should be reflected through the abstract method:

boolean executePayment(double cost)

Payments

💻 Information for each payment will be contained in the PaymentInfo class:

-->
package bg.sofia.uni.fmi.mjt.virtualwallet.core.payment;

public class PaymentInfo {

    public PaymentInfo(String reason, String location, double cost) {
        // constructor implementation
    }

    public double getCost() {
        // method implementation
    }

    public String getReason() {
        // method implementation
    }

    public String getLocation() {
        // method implementation
    }
}
<--


Validation

☑️ Pay attention to the methods in VirtualWallet and consider when they would return false. Implement suitable validation for the parameters these methods accept.

Bonus Task

Store the last 10 transactions made through the virtual wallet. Include:

Card name from which the transaction (payment) was made
Date of the transaction
Information about the payment itself, i.e., PaymentInfo.
👉 When there is no more space for storage, remove the oldest transaction.

👉 For working with date and time, you can use the java.time API, paying special attention to the LocalDateTime class and its methods.
