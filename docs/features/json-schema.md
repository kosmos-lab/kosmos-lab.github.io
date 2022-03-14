## JSON-Schema

Every Device/Entity can and should have an accompanying [JSON-Schema](https://json-schema.org/) that defines its properties and possible states. The platform validates every input against the JSON-Schema and guarantees that no invalid state can be set. Depending on the source of the request and the given parameters the platform can try to fix erroneous states by removing unwanted properties, changing the type of the parameter, or choosing the next value that would be in the valid range.

???+ check "stable"
    This core feature is stable and heavily tested in production use.
