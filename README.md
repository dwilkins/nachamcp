# Nachamcp

NachaMCP is an MCP Server to allow LLMs to reason about ACH records.  NachaMCP will
parse ach records into JSON or Markdown, as requested by the LLM.

## Installation


```bash
gem install nachamcp
```
To enable for Gemini CLI (`.gemini/settings.json`):
```json
{
  "mcpServers": {
    "nachamcp": {
      "command": "nachamcp"
    }
  }
}
```

## Usage

Give me a detailed count of the record types in these ach records
```
101 02601507911223344552006011330A094101GS BANK USA            YOUR COMPANY NAME      REF123AB
5220ALPHA COMPANY                       1234567890CCDPAYROLL   JUN 20200701   1026015070000001
632111122223123456789        0000100000AB156325       JACK SMITH              0026015070000001
632111122223123456789        0000100000AB156325       JACK SMITH              0026015070000002
632111122223123456789        0000100000AB156325       JACK SMITH              0026015070000003
822000000300333366660000000000000000003000001234567890                         026015070000001
5220ALPHA COMPANY                       1234567890PPDPAYROLL   JUN 20200701   1026015070000002
632111122223123456789        0000100000AB156325       JACK SMITH              0026015070000011
632111122223123456789        0000100000AB156325       JACK SMITH              0026015070000012
822000000200222244440000000000000000002000001234567890                         026015070000002
5220ALPHA COMPANY                       1234567890PPDPAYROLL   JUN 20200701   1026015070000003
632111122223123456789        0000100000AB156325       JACK SMITH              0026015070000101
632111122223123456789        0000100000AB156325       JACK SMITH              0026015070000102
822000000200222244440000000000000000002000001234567890                         026015070000003
9000003000002000000070077785554000000000000000000700000
```

### Without NachaMCP:
```
Of course. Here is a detailed breakdown of the record types in the data you provided:

  ┌──────────────────┬──────────────────┬───────┐
  │ Record Type Code │ Record Type Name │ Count │
  ├──────────────────┼──────────────────┼───────┤
  │ 101              │ File Header      │ 1     │
  │ 5220             │ Batch Header     │ 3     │
  │ 632              │ Entry Detail     │ 6     │
  │ 8220             │ Batch Control    │ 3     │
  │ 900              │ File Control     │ 1     │
  │ Total            │                  │ 14    │
  └──────────────────┴──────────────────┴───────┘
```

### With NachaMcp

```
 Of course. Here is a detailed count of the record types in the ACH records you provided:

   * file_header: 1
   * batch_header: 3
   * ccd_entry_detail: 3
   * ppd_entry_detail: 4
   * batch_control: 3
   * file_control: 1
```

## Development

After checking out the repo, run `bin/setup` to install dependencies. Then, run `rake spec` to run the tests. You can also run `bin/console` for an interactive prompt that will allow you to experiment.

To install this gem onto your local machine, run `bundle exec rake install`. To release a new version, update the version number in `version.rb`, and then run `bundle exec rake release`, which will create a git tag for the version, push git commits and the created tag, and push the `.gem` file to [rubygems.org](https://rubygems.org).

## Contributing

Bug reports and pull requests are welcome on GitHub at https://github.com/dwilkins/nachamcp. This project is intended to be a safe, welcoming space for collaboration, and contributors are expected to adhere to the [code of conduct](https://github.com/dwilkins/nachamcp/blob/master/CODE_OF_CONDUCT.md).

## License

The gem is available as open source under the terms of the [MIT License](https://opensource.org/licenses/MIT).

## Code of Conduct

Everyone interacting in the Nachamcp project's codebases, issue trackers, chat rooms and mailing lists is expected to follow the [code of conduct](https://github.com/dwilkins/nachamcp/blob/master/CODE_OF_CONDUCT.md).
