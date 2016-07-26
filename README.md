# icao_db

Sqlite3 database of icao mode_s codes, aircraft type, and tail numbers.

This was created for use with my [version of dump1090](https://github.com/RobAltenburg/dump1090) to look up additional information.

This is set up so that only the mode_s code is a primary key.  A given tail number might have
more than one mode_s code associated with it.  This may be because of outright errors in the
source material, but it could also reflect transponders that have been moved to a different
aircraft.

The db consists of a single table defined as follows:

    CREATE TABLE "aircraft"
    (
    mode_s TEXT PRIMARY KEY,  -- hex value of icao mode_s code in lowercase text
    tail_num TEXT,            -- "N-number" in the US
    mfg TEXT,                 -- manufacturer
    model TEXT,               -- Using abbreviations where possible
    updated INT,              -- unixtime of inclusion or last confirmation of info.
    comment TEXT              -- normally a more detailed description
    );

