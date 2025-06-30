# Security and authorization

Authorization and transport security features described in the BCP-003 family and in IS-10 are used to secure and authorize this protocol.

The relevant documents can be found here:

- [AMWA BCP-003-01 Secure Communication in NMOS Systems](https://specs.amwa.tv/bcp-003-01)
- [AMWA BCP-003-02 Authorization in NMOS Systems](https://specs.amwa.tv/bcp-003-02)
- [AMWA BCP-003-03 Certificate Provisioning in NMOS Systems](https://specs.amwa.tv/bcp-003-03)
- [AMWA IS-10 NMOS Authorization Specification](https://specs.amwa.tv/is-10)

More specifically [BCP-003-02](https://specs.amwa.tv/bcp-003-02/releases/v1.0.0/docs/1.0._Authorization_Practice.html#nmos-apis) has dedicated sections for how JSON Web Tokens can be created.

Note that the `.` character is specifically used as a delimiter in role paths included in the read/write claims, so it cannot be used inside object roles.
