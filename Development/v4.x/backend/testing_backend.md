# Testing

## Packages
Following is the list of hte main packages used to build, run and manage testing for the project

* [Chai](https://github.com/chaijs/chai) - Assertion
* [Supertest](https://github.com/visionmedia/supertest) - NodeJS testing for HTTP calls
* [Mocha](https://github.com/mochajs/mocha) - Test runner framework

## API tests

SciCat backend v4.x comes with many API tests. They are locate in the `/test` folder

In order to run the tests you need to have the backend running.  
In a different terminal, you can run one of the following two commands:

`npm run test`

or 

`mocha --config ./test/config/.mocharc.json --timeout=5000 --reporter=nyan`

If you are interested in a specific subset of tests, you can add the _--grep_ option to the mocha command.  
For example if you are interested in running only the test named _Authorization functionalities_, you can use the following command:  
`mocha --config ./test/config/.mocharc.json --grep \"Authorization functionalities\ --timeout=5000 --reporter=nyan`

## Coverage

The following is the list of the current tests groups. We are trying to cover all the different components and endpoints of SciCat backend v4.x and we keep adding new tests every release cycle.
The coverage might not be complete. If you find any use case  that is not covered by our tests, feel free to open an issue or, even better, to write a new set of tests and submit a PR.

List of tests:
| test file | main code | title | description |
| ----- | ----- | ----- | ----- |
| Auth.js | 0100 |  Authorization functionalities| Test login and logout for functional accounts |
| CheckDifferentDatasetTypes.js | 0200 | CheckDifferentDatasetTypes |  | 
| DatasetAuthorization.js | 0300 |  |  |
| DatasetFilter.js | 0400 |  |  |
| DatasetLifecycle.js | 0500 |  |  |
| DerivedDatasetDatablock.js | 0600 |  |  |
| DerivedDataset.js | 0700 | Derived Datasets | test derived datasets functionalities |
| DerivedDatasetOrigDatablock.js | 0800 | DerivedDatasetOrigDatablock | Test OrigDatablocks and their relation to derived Datasets |
| Instrument.js | 0900 | Instrument | instrument management, creation, update, deletion and search |
| InstrumentsFilter.js | 1000 |  |  |
| Jobs.js | 1100 |  |  |
| LoginUtils.js | 1200 |  |  |
| Policy.js | 1300 |  |  |
| ProposalAuthorization.js | 1400 |  |  |
| Proposal.js | 1500 |  |  |
| PublishedData.js | 1600 |  |  |
| RandomizedDatasetPermissions.js | 1700 |  |  |
| RawDatasetDatablock.js | 1800 |  |  |
| RawDataset.js | 1900 |  |  |
| RawDatasetOrigDatablock.js | 2000 |  |  |
| ResetDataset.js | 2100 |  |  |
| Sample.js | 2200 |  |  |
| UserAuthorization.js | 2300 | User Authorization | test that user authorization are correct |
| Users.js | 2400 |  |  |

## Test data

It is our intention to save all test data in the file `TestData.js`.  
In some cases, we need to code variation of the data directly in the test file.

## Test accounts

Tests are performed assuming the following user accounts, groups and configuration are present.
Users and groups are defined in the configuration structre defined in ```src/config/configuration.ts```.
These settings are meant only for testing and to demonstrate the capabilities of backend V4.x. IT is highly recommended to remove accounts that are not needed and change passwords and group affiliations as needed.

### Accounts
| Account | Groups | Is Admin | Can Delete | Can Create Dataset |
| ----- | ----- | ----- | ----- | ----- |
| admin | admin, global | yes | no | Any |
| ingestor | ingestor | yes | no | Any |
| archiveManager | archivemanager | yes | yes | no |
| proposalIngestor | proposalingestor | no | no | no |
| user 1 | group1 | no | no | Own |
| user 2 | group2 | no | no | Own |
| user 3 | group3 | no | no | Own |
| user 4 | group4 | no | no | no |

### Group permissions
| Environmental variable | List of groups |
| ----- | ----- | 
| ADMIN_GROUPS | admin, ingestor, archivemanager |
| DELETE_GROUPS | archivemanager |
| CREATE_DATASET_GROUPS | group1,group2,group3 |


## Test Details

This section provides details on how all the tests files listed above are organized. Each subsection, provides a list of the test included in each file and the details of each one of them.

- [Datasets]() 
- [0900: Instrument](./testing/instrument.md)
- [2300: User Authorization](./testing/user_authorization.md)

