# adonis-audit
Audit models in AdonisJS

## DISCLAIMER

This is just a release for using it through NPM. Not claiming any rights over the original code developed.

## How to use

Install npm module:

```bash
$ adonis install adonis-audit
```

## Register provider

Once you have installed adonis-audit, make sure to register the provider inside `start/app.js` in order to make use of it.

```js
const providers = [
  'adonis-audit/providers/AuditProvider'
]
```

## Using the module:

Add the following to your model's `boot` method:

```js
class MyModel extends Model {
  static boot () {
    super.boot()
    this.addTrait('@provider:Auditable')
  }
}
```

This you can start using as follows:

```js
// create
const model = await MyModel.audit().create({name: 'John'})

// update
const model = MyModel.find(1)
await model.audit().update({name: 'Simon'})

// delete
const model = MyModel.find(1)
await model.audit().delete()
```

## Built With

* [AdonisJS](http://adonisjs.com) - The web framework used.

## Versioning

[SemVer](http://semver.org/) is used for versioning. For the versions available, see the [tags on this repository](https://github.com/simontong/adonis-auditable/tags).  

## Authors

* **Simon Tong** - *Developer* - [simontong](https://github.com/simontong)

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.


## Changelog
- v2.0.2
  - Fixed bugs for AdonisJS 4.1.
  
- v2.0.1
  - Removed need to pass in `ctx` parameters.
  - Update README and instructions.md files.

- v2.0.0
  - Removed ctx injection on boot. `ctx` parameters need to be passed in manually now.
  - Updated README to reflect new changes.
  - Added this changelog.

- v1.0.1
  - Initial release.
