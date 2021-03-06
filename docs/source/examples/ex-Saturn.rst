Saturn examples
***************

Let's define a small helper function::

    def print_me(msg, val):

        print("{}: {}".format(msg, val))

We can compute the geometric heliocentric position for a given epoch::

    epoch = Epoch(2018, 10, 27.0)

    lon, lat, r = Saturn.geometric_heliocentric_position(epoch)

    print_me("Geometric Heliocentric Longitude", lon.to_positive())

    # Geometric Heliocentric Longitude: 279.5108

    print_me("Geometric Heliocentric Latitude", lat)

    # Geometric Heliocentric Latitude: 0.6141

    print_me("Radius vector", r)

    # Radius vector: 10.06266

Compute the geocentric position for 1992/12/20::

    epoch = Epoch(1992, 12, 20.0)

    ra, dec, elon = Saturn.geocentric_position(epoch)

    print_me("Right ascension", ra.ra_str(n_dec=1))

    # Right ascension: 21h 11' 41.8''

    print_me("Declination", dec.dms_str(n_dec=1))

    # Declination: -17d 15' 40.8''

    print_me("Elongation", elon.dms_str(n_dec=1))

    # Elongation: 46d 51' 47.7''

Print mean orbital elements for Saturn at 2065.6.24::

    epoch = Epoch(2065, 6, 24.0)

    l, a, e, i, ome, arg = Saturn.orbital_elements_mean_equinox(epoch)

    print_me("Mean longitude of the planet", round(l, 6))

    # Mean longitude of the planet: 131.196871

    print_me("Semimajor axis of the orbit (UA)", round(a, 8))

    # Semimajor axis of the orbit (UA): 9.55490779

    print_me("Eccentricity of the orbit", round(e, 7))

    # Eccentricity of the orbit: 0.0553209

    print_me("Inclination on plane of the ecliptic", round(i, 6))

    # Inclination on plane of the ecliptic: 2.486426

    print_me("Longitude of the ascending node", round(ome, 5))

    # Longitude of the ascending node: 114.23974

    print_me("Argument of the perihelion", round(arg, 6))

    # Argument of the perihelion: -19.896331

Compute the time of the conjunction close to 2125/6/1::

    epoch = Epoch(2125, 6, 1.0)

    conj = Saturn.conjunction(epoch)

    y, m, d = conj.get_date()

    d = round(d, 4)

    date = "{}/{}/{}".format(y, m, d)

    print_me("Conjunction date", date)

    # Conjunction date: 2125/8/26.4035

Compute the time of the opposition close to -6/9/1::

    epoch = Epoch(-6, 9, 1.0)

    oppo = Saturn.opposition(epoch)

    y, m, d = oppo.get_date()

    d = round(d, 4)

    date = "{}/{}/{}".format(y, m, d)

    print_me("Opposition date", date)

    # Opposition date: -6/9/14.3709

Compute the time of the station in longitude #1 close to 2018/11/1::

    epoch = Epoch(2018, 11, 1.0)

    sta1 = Saturn.station_longitude_1(epoch)

    y, m, d = sta1.get_date()

    d = round(d, 4)

    date = "{}/{}/{}".format(y, m, d)

    print_me("Date of station in longitude #1", date)

    # Date of station in longitude #1: 2018/4/17.9433

Compute the time of the station in longitude #2 close to 2018/11/1::

    epoch = Epoch(2018, 11, 1.0)

    sta2 = Saturn.station_longitude_2(epoch)

    y, m, d = sta2.get_date()

    d = round(d, 4)

    date = "{}/{}/{}".format(y, m, d)

    print_me("Date of station in longitude #2", date)

    # Date of station in longitude #2: 2018/9/6.4175

Find the epoch of the Perihelion closer to 2000/1/1::

    epoch = Epoch(2000, 1, 1.0)

    e = Saturn.perihelion_aphelion(epoch)

    y, m, d, h, mi, s = e.get_full_date()

    peri = str(y) + '/' + str(m) + '/' + str(d) + ' at ' + str(h) + ' hours'

    print_me("The Perihelion closest to 2000/1/1 happened on", peri)

    # The Perihelion closest to 2000/1/1 happened on: 2003/7/26 at 15 hours

Compute the time of passage through an ascending node::

    epoch = Epoch(2019, 1, 1)

    time, r = Saturn.passage_nodes(epoch)

    y, m, d = time.get_date()

    d = round(d, 1)

    print("Time of passage through ascending node: {}/{}/{}".format(y, m, d))

    # Time of passage through ascending node: 2034/5/30.2

    print_me("Radius vector at ascending node", round(r, 4))

    # Radius vector at ascending node: 9.0546

Compute the approximate magnitude of Saturn::

    sun_dist = 9.867882

    earth_dist = 10.464606

    delta_u = Angle(16.442)

    b = Angle(4.198)

    m = Saturn.magnitude(sun_dist, earth_dist, delta_u, b)

    printi_me("Approximate magnitude of Saturn", m)

    # Approximate magnitude of Saturn: 1.9

Compute the ring inclination::

    epoch = Epoch(1992, 12, 16.00068)

    i = Saturn.ring_inclination(epoch)

    print_me("Saturn's ring inclination", round(i, 6))

    # Saturn's ring inclination: 28.076131

Compute the longitude of the ascending node of the ring::

    epoch = Epoch(1992, 12, 16.00068)

    omega = Saturn.ring_logitude_ascending_node(epoch)

    print_me("Saturn's ring longitude of the ascending node", round(omega, 6))

    # Saturn's ring longitude of the ascending node: 169.410243

Compute the parameters related to the ring::

    epoch = Epoch(1992, 12, 16.00068)

    B, Bprime, P, delta_U, a, b = Saturn.ring_parameters(epoch)

    print_me("Saturnicentric latitude of the Earth", round(B, 3))

    # Saturnicentric latitude of the Earth: 16.442

    print_me("Saturnicentric latitude of the Sun", round(Bprime, 3))

    # Saturnicentric latitude of the Sun: 14.679

    print_me("Geocentric position angle of nothern semiminor axis", round(P, 3))

    # Geocentric position angle of nothern semiminor axis: 6.741

    print_me("Difference in Saturnicentric longitudes of Sun and Earth", round(delta_U, 3))

    # Difference in Saturnicentric longitudes of Sun and Earth: 4.198

    print_me("Size of major axis of outer ring", round(a, 2))

    # Size of major axis of outer ring: 35.87

    print_me("Size of minor axis of outer ring", round(b, 2))

    # Size of minor axis of outer ring: 10.15
