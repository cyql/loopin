# Design

/teams
    {
        name
        users {
            references to /users/UUID (?)
        }
        default_check_in_time
        goal_tracking (y/n)
        admins {
            references to /users/UUID
        }
        observers {
            references to /users/UUID
        }
        

    }

/users
    {
        whatever firebase has +
        timezone
        we should own this data though
        teams {
            reference to /teams/UUID (?) that a user belongs to
        }
    }

/user_preferences (?)
    {
        preferred check-in time (overrides from team)
    }

/checkin
    {
        teamUUID__DATE {
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