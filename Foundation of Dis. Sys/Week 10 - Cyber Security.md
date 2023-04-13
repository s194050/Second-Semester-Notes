* C.I.A
	* Confidentiality
	* Integrity
	* Availability
* A.A.A
	* Assurance
		* Refers to how trust is provided and managed
		* Tools: Policies, Permissions, Protections
	* Authenticity
		* The ability to determine that statements, policies and permissions issued by persons or systems are genuine/authentic
		* Can be seen as authentication + integrity
		* Primary tool: Digital signatures - Used to achieve non-repudiation
	* Anonymity
		* The property that certain records or transactions not to be attributable to any individual
		* Tools: Proxies, Pseudonyms, Aggregation, Mixing

* Asset
	* Any data, device, or other component of the environment that supports information-related activities
		* Examples:
			* Hardware - Servers, etc
			* Software - Mission critical systems, etc
			* Confidential data
* Vulnerability
	* Weakness that can be unintentionally or intentionally exploited to damage assets
		* Examples:
			* Weak passwords
			* Programs with known flaws
			* Etc
* Threat
	* Potential negative action or event facilitated by a vulnerability that results in an unwanted impact to an asset (such as an computer system or application)
	* They can be unintentional(Natural disaster) or intentional(Hacking)
		* Can be modelled by Microsoft's STRIDE
* Attack
	* Sequence of steps needed to realise a threat - The implementation of a threat

* Types of attacks
	* Eavesdropping - Threat to confidentiality
	* Man-in-the-middle - Threat to confidentiality and integrity
	* Denial of Service (DoS) - Threat to availability
	* Masquerading - Threat to authenticity (Pretending to be somebody else)
	* Repudiation - Threat to authenticity, integrity, availability and more, but depends on the malicious action
	* Correlation and Traceback - Threat to authentication
		* The integration of multiple data sources and information flows to determine the source of a particular data stream or piece of information

* PKI's solve the "spoofing others' identities" attack based on digital signatures
	* It consists of a RA and a CA. 
	* This structure provides a source of trust
	* Every CA should have a CPS
* We need to this bind an identity to a specific key.  This allows communication to only have to trust the CA.
* ![[Pasted image 20230413143636.png|400]]

* 