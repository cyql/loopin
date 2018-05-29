# Firestore Design

/account

    {
        UUID
        name
        teams {}
        users {}
        owner {}+
        created on/by
        updated on/by
        deleted on/by
    }


/account_subscription

    {
        do we even need to keep track of this or would it just be related to the account UUID in Stripe (or whatever)
    }

/teams

    {
        UUID
        name
        default_timezone
        default_check_in_time
        collection_days (M,T,W,R,F,S,U)
        members {
            references to /users/UUID (?)
        }
        questions {
            previous (`What did you accomplish %{previous_period}?`)
            next (`What are your goals for %{next_period}?`)
            impediments (`Any obstacles impeding you from meeting your goals?`)
        }
        goal_tracking (y/n)
        activity_as_participation // `Enable activity as participation` With this option enabled, team members with external activity will be automatically marked as checked-in, even if they haven't anred the check-in questions.
        show_report_graphs
        admins {
            references to /users/UUID
        }
        observers {
            references to /users/UUID
        }
        notifications {
            reminder_time
            summary_time
            Send_summary_the_next_day // sends summary the next day at `summary_time`
        }
        created on/by
        updated on/by
        deleted on/by (active unless deleted)
    }

/users

    {
        UUID
        whatever firebase has (we should own this data though... don't use Slack's account/user structure for example)
        timezone
        teams {
            reference to /teams/UUID (?) that a user belongs to
        }
        notifications {

        }
        unavailable_dates { // absent, vacation

        }
        created on/by
        updated on/by
        deleted on/by
    }

/checkin

    {
        teamUUID__DATE {
            [
                user
                date
                time
                previously
                met_goals_met
                currently/next
                impediments
                created on/by
                updated on/by
                deleted on/by
            ]
        }
    }
