# Lyra : Definition of the ID for Alastria

## ANS - Alastria Name Service

alastria.users.<alias> aka @<alias>
alastria.<brand>

Each brand will need to deploy a Smart contract acting as a resolver for its own domain.
Based on ENS but with a different way of giving names

## Alastria ID

Process to create a new ID : Only identified IDs can create a new IDs in Alastria now (That's a paradox, I know). First ID to be created is Alastria itself, this iD will be able to create new organitzations.

We will be using uPOrt Smart Contracts a s a basis for our Identity System. We will use two main components : IdentityRegister (uPortRegister) and IdentityManager.

Identity Register :


IdentityManager


### Genesis

At the beginning of times we have one addres (addr0) to act as main admin for the system. It's importnat to keep that address safe (of course). IN a later stage we will turn the contracts multiowner so we don't tdepend on this unqieu address.

1. Deploy the uPort Like Contract for Alastria.
2. Deploy the Generic register for attributes.
3. Write a generic attribute for ALastria
4. Deploy the Generic ANS for Alastria
5. Deplot the Resolver for Alastria

### We need tools (nodejs/python) to :

1. Deploy Smart Contracts easliy
2. Deploy Ids
3. Write entries in the Alastria NS
4. Write entries to the Resolvers

### At this point we will have

1. Address for ANS
2. Address for Alastria main ID
3. Address for teh Alastria Resolver
4. We can resolve "alastria" to the Alastria main ID address

### Add another ID (from the console)

1. Deploy the uPort Like Contract for the new Organization (Org1)
2. Cgange the owners of the Org1 ID
3. Write a generic attribute for Org1 (name and adrress, signed by addr0)
4. Write entries in the Alastria NS
5. Deploy the Resolver for org1

### At this point we will have

1. Address for ANS and entries for Alastria and Org1
2. Address for Alastria main ID and Org1
3. Address for the Org1 Resolver
4. We can resolve "alastria.org1" to the Org1 ID address

### The API

To make things easier for this organizations to add users in their zones we will create an API so they can (once authenticated) deploy easily new IDs.

/login
We will use webtokens (jwt).

.... define process... Need to talk to you guys on slack

/newId/<addr_owner>/<name>
Deploys a new ID and sets the owner to <addr_owner>. Adds a new entry to the resolver with the name. Returns the new <addr> for the ID.

/registerAttribute/<addr>/<attribute>
Adds an atribute to the <addr>

## Alastria ID App : On the phone!
Double verification : email + SMS (phone)
We will need a double verification to create a new Identity. The app will ask for the Phone Number and will send a verification code via SMS. The app will also ask for an email and will send a code to the email.

Once the App is verified we can save basic information about the user : First Name and last names (we have 2 in Spain), address, gender and date of birth.

1. Create a Smart contract representing your ID
2. Create a file (JSON) with all your data following the standar Persona. We create a merkle tree of all the information. This way we can share anly the information we want to share and the hashes for other information. A nonce will be added whenever needed (DNI) for security reasons.
3. Write in the registry the top of the merkle tree. AT this point thins information is not certified by anyone (not trutsable)
4. Ask for an alias and create the alias in the ANS.
