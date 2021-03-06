# ExVictorOps

[![Hex.pm](https://img.shields.io/hexpm/v/ex_victor_ops.svg)](https://hex.pm/packages/ex_victor_ops)
[![Build Status](https://travis-ci.org/cagedata/ex_victor_ops.svg?branch=master)](https://travis-ci.org/cagedata/ex_victor_ops)
[![Doc Status](https://inch-ci.org/github/cagedata/ex_victor_ops.svg?branch=master)](https://inch-ci.org/github/cagedata/ex_victor_ops)
[![Coverage Status](https://coveralls.io/repos/github/cagedata/ex_victor_ops/badge.svg?branch=)](https://coveralls.io/github/cagedata/ex_victor_ops?branch=)


Gain access to your favorite On-Call management tool from your favorite language. ExVictorOps lets
you program against the [VictorOps](http://victorops.com) API to make On-Call suck even less by integrating it into the
programs you're already using.

## Installation

ExVictorOps is currently very beta software. You can install it from Hex:

    def deps do
      [
        { :ex_victor_ops, "~> 0.2.0" }
      ]
    end

Or from GitHub:

    def deps do
      [
        { :ex_victor_ops, "cagedata/ex_victor_ops" }
      ]
    end

And then ensure that it starts up before you application:

    def application do
      [applications: [:ex_victor_ops]]
    end

## Configuration

You will need to set the following configuration variables in your `config/config.exs` file:

    use Mix.Config

    config :ex_victor_ops, api_id: "YOUR_API_ID",
                           api_key: "YOU_API_KEY"

To find your API key and ID open the [VictorOps Portal](https://portal.victorops.com) and navigate to Settings -> API.

## Usage

ExVictorOps will come with modules to support each of the [VictorOps API endpoints](portal.victorops.com/public/api-docs.html):

### On-Call

`ExVictorOps.OnCall` give access to user and team on-call schedules:

    # Get a team's on-call schedule
    ExVictorOps.OnCall.get_team "support"
    # => %ExVictorOps.Entities.OnCall{...}

    # Get today's on-call schedule for a team
    ExVictorOps.OnCall.get_team "support", %{days_forward: 0}
    # => %ExVictorOps.Entities.OnCall{...}

    # Get a user's on-call schedule:
    ExVictorOps.OnCall.get_user "davejlong"
    # => [%ExVictorOps.Entities.OnCall{...}]

## Contibuting

See [CONTRIBUTING.md](CONTIBUTING.MD) for contribution guidelines.

## License

ExVictorOps is licensed under the MIT license. For more details, see the [LICENSE](LICENSE) file at the root of the repository. ExVictorOps depends on various libraries which have their own licenses.

VictorOps is trademark of VictorOps, Inc.
