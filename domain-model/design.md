# Design

/teams
    {
        name
        users {
            references to /users/UUID (?)
        }
        default_check_in_time
        goal_tracking (y/n)

    }

/users
    {
        whatever firebase has +
        timezone
        we should own this data though
    }

/user_preferences (?)
    {
        preferred check-in time (override from )
    }

/checkin
    {
        team_UUID {
            user
            date
            time
            previously
            met_goals_met
            currently
            impediments
            created on/by
            updated on/by
            deleted on/by
        }
    }