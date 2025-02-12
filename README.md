YANG identity example for AXdz

The purpose is to show how to create an equivalent ifType name by basing a new identity on an existing identity.

ident.yang:  This is the positive example.  An identity called ieee8021axLag is created with a base of ianaift:ieee8023adLag.  Instances are created that show that both ieee8021axLag and ieee8023adLag can be used and the ieee802-dot1q-bridge.yang module when statement doesn't have to change.
- m.in:  Expect script that runs yanglint
- m.json: Example instance data, containing two use-cases (one using ieee8021axLag and the other using ieee8023adLag)
- m.out:  Shows the json converted to XML, indicating the instance data is correct

ident-alt.yang:  This is an alternative, that doesn't work unless ieee802-dot1q-bridge.yang changes.  There is a new identity created called ieee-link-agg and a new identity called ieee8021axLag.  The identity ieee-link-agg has both ieee8021axLag and ieee8023adLag as bases.  This would work if the ieee802-dot1q-bridge.yang module could change to use the ieee-link-agg identity in the when statement, and modify the IANA registry to add a base to ieee8023adLag (see ident-mod  example).
- m-alt.in: Expect script that runs yanglint
- m-alt.json: Example instance data that is identical to the m.json examples (slight modifications because of namespace differences)
- m-alt.out: Shows the error messages because the when statement is not satisfied.

ident-mod.yang:  This is the positive example.  This modifies the when statement in ident-alt.yang to show this is viable if ieee802-dot1q-bridge.yang is modified.
- m-mod.in:  Expect script that runs yanglint
- m-mod.json: Example instance data that is identical to the m.json examples (slight modifications because of namespace differences)
- m-mod.out:  Shows the json converted to XML, indicating the instance data is correct
