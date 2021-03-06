# COVID-19Pact LACChain task force

COVID-19PAct® is a task force where different LACChain partners collaborate to lead a campaign to provide useful blockchain-based solutions to combat the spread of the Coronavirus. The goal is to:

* Propose a standard for the forms and the verifiable credentials that are generated by different mobile apps to notarize information about isolation periods.

* Create a single smart contract that will register all the cryptographyc proofs of the credentials so every app whitelisted can register the proofs on it, and everyone can verify them against it.

* Create a map where pseudonymous citizens are displayed with different colors depending on if they are health and isolated (green), interruption isolation for a permitted reason (yellow), with symptoms (orange), or infected (red). The only information that is collected is age, gender, location, and information to notarize.

## 1. Definition of the information to be notarized 

We are proposing to have four different forms to notarize: 

* Confinement [ESP version] [ENG version] 
* Interruption of confinement [ESP version] [ENG version] 
* Symptoms [ESP version] [ENG version] 
* Infection [ESP version] [ENG version] 

Click on the links to see them and provide feedback. 

## 2. Data formats and verifiable credential standards 

We are proposing to create a common format aligned with W3C, DIF, EBSI, and others in which the information of the forms provided by the citizens via UI will be embedded and understood by all wallets.  
Additional requirements for the credentials are: 

* They have to be signed by the same private key that corresponds to the app/digital wallet that was used to generate them. 

* The hash of the credential, time-stamp, expiration date, public key of the app that generated it, gender of the person, age of the person, location of the person (adding latitude and longitude), and type of information attested (isolation, interruption of isolation and reason, symptoms, or infection) has to be send to a common smart contract deployed on the blockchain and described in Section 3. 

* No information other than the indicated in the previous bullet point can be kept by the provider of the app. Therefore, the provider of the app won’t keep a copy of the credentials in its repositories. 

* In order to verify the credentials, the proof mechanism will consist of checking against the smart contract that the hash/id of the credential was registered in that smart contract, the time-stamp, and the expiration date. 

## 3. Verification of credentials

We are proposing to deploy a single smart contract in the LACChain Blockchain Network (Hyperledger Besu) where only those apps validated (by the IDB team of LACChain) will be able to write. In this smart contract, therefore, the IDB LACChain team will whitelist the address of those apps validated. This apps will be therefore authorized to register the hashes of the credentials they generate in the smart contract and anyone will be able to verify the credentials against the smart contract. That allows any of the app/digital wallet involved in this collaborative effort to verify credentials issued by others as (i) they all use the same format for the verifiable credentials, and (ii) they all verify them against the same smart contract, and (iii) they trust the IDB to only whitelist trusted apps to register credentials id’s in the smart contract.

In this smart contract, the apps will register the following information of each credential they generate: 

*	Hash of the credential 
*	Time-stamp 
*	Expiration date 
*	Public key of the app that generated it 
*	Gender of the person 
*	Age of the person 
*	Location of the person 
*	Type of information attested (isolation, interruption of isolation and reason, symptoms, or infection)  

As explained before, the three first items will be used to verify the credential, the fourth item will used to monitor how much is each app being used, and the other items will be used to monitor pseudonymous information as explained in the following Section. 

![Verification of credentials](/docs/verification_covid.png)

## 4. Presentation of the pseudonymized data
 
We are proposing the have an external service listening events to get the public information that has been registered in the blockchain consisting of: 

*	Public key of the app that generated it 
*	Gender of the person 
*	Age of the person 
*	Location of the person 
*	Type of information attested (isolation, interruption of isolation and reason, symptoms, or infection)  

This service will be subscribed to events in the smart contract. The idea is to create and display a map that plots points of three different colours in the location where the information has been notified. This colours would be: 

*	Green for isolation 
*	Yellow for interruption of isolation 
*	Orange for symptoms 
*	Red for infection 

When one clicks on the points/region, it should be able to see information of the gender/age of the person (it can be on average or individually, depending of the number of people reporting).

We are also proposing to generate dashboards indicating, at least: 

*	How many credentials have been generated. 
*	Where (location of the citizen) are the credentials being generated (and therefore the info notarized). 
*	How many credentials generated each app. 
*	How many credentials have been generated of each type. 
*	A classification by frequency of the reasons why people interrupt isolation (from credential #2). 

![Presentation of credentials](/docs/presentation_covid.png)

## 5. Privacy ensured

Only the citizens own the credentials and have all the information they provide. Nobody else (nor the app provider, the blockchain network, or the map displaying the data) has any information other than: 

*	Gender 
*	Age 
*	Location 
*	Type of information attested (isolation, interruption of isolation and reason, symptoms, or infection) 
 
## 6. Authentication of citizens at the application level

Apps/digital wallets are required to authenticate citizens using a two-factor authentication. We recommend using something that you have (the phone itself, but receiving an SMS) and something you know (a password). Idemia is also providing free linceses to leverage their biometric proof of live solution via SDK.





