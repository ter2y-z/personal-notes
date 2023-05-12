# Update BFF after Xplore-API is Updated
We're using schema first approach for BFF side.
## Look into updates on [xplore-api](https://github.com/anzx/xplore-api) update
1. Keep an eye on `./openapi/controls/` and `./openapi/outcome` folders, while the latter one is for Cases and the former one is for the rest parts.
2. In `./openapi/controls.yaml` we can find the details of the controls' api: [path](https://github.com/anzx/xplore-api/blob/8574cb3fbd17e253ebbff3c6b47bd6e9bf69640b/openapi/controls/controls.yaml#L27) | [components(parameters / response / schemas)](https://github.com/anzx/xplore-api/blob/8574cb3fbd17e253ebbff3c6b47bd6e9bf69640b/openapi/controls/controls.yaml#L408)
3. Schemas should be focused for the later graphql update

## Update BFF(xplore-backend)

### Update graphql schema
1. Update or create new definitions to `./xplore-node/src/graphqls/types/*.graphql`. The name should be match the ones under `./openapi/controls/*.yaml`. (e.g. **/asset.graphql** and **/asset.yaml**).
2. Update `./xplore-node/src/graphqls/queries.graphql` when getting data
3. Update `./xplore-node/src/graphqls/mutations.graphql` when editing data
4. Run `npm run gen:schema`
5. Run `npm run gen:types`

### Update resolver
1. Update the related resolver. You may notice something like `@Query('assets')` sitting in the resolver files. `assets` in this case can be found in `./xplore-node/src/graphqls/queries.graphql`.
2. Different xapi functions can be found in `./xplore-node/src/xplore-api/xplore-api.service.ts` - such as `findAll` / `findById` / `create` etc.
  ```javascript
  @Query('evidence')
  async getEvidence(@Args('id') id: string): Promise<Evidence> {
    return this.xapi
      .findById<EvidenceModel>(Resource.Evidence, id)      // get data from xplore-api by using id and ./xplore-node/src/xplore-api/routes.ts
      .then(unwrap)                                        // unwrap data
      .then(e => Object.assign(new Evidence(), e));        // assign data to graphql
  }
  ```
 
### Excel part on BFF
1. It's located at `./xplore-node/src/controllers/excel.controller.ts`.
2. This part is using RESTful since graphql is not good at uploading files.
3. Use @Body() for the filter data.
