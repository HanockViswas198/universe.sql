# universe.sql
This is the Sample Database of Universe created using Postdegree SQL as a part of Relational Data Base Projecr 

--
-- PostgreSQL database dump
--

-- Dumped from database version 12.17 (Ubuntu 12.17-1.pgdg22.04+1)
-- Dumped by pg_dump version 12.17 (Ubuntu 12.17-1.pgdg22.04+1)

SET statement_timeout = 0;
SET lock_timeout = 0;
SET idle_in_transaction_session_timeout = 0;
SET client_encoding = 'UTF8';
SET standard_conforming_strings = on;
SELECT pg_catalog.set_config('search_path', '', false);
SET check_function_bodies = false;
SET xmloption = content;
SET client_min_messages = warning;
SET row_security = off;

DROP DATABASE universe;
--
-- Name: universe; Type: DATABASE; Schema: -; Owner: freecodecamp
--

CREATE DATABASE universe WITH TEMPLATE = template0 ENCODING = 'UTF8' LC_COLLATE = 'C.UTF-8' LC_CTYPE = 'C.UTF-8';


ALTER DATABASE universe OWNER TO freecodecamp;

\connect universe

SET statement_timeout = 0;
SET lock_timeout = 0;
SET idle_in_transaction_session_timeout = 0;
SET client_encoding = 'UTF8';
SET standard_conforming_strings = on;
SELECT pg_catalog.set_config('search_path', '', false);
SET check_function_bodies = false;
SET xmloption = content;
SET client_min_messages = warning;
SET row_security = off;

SET default_tablespace = '';

SET default_table_access_method = heap;

--
-- Name: exoplanet; Type: TABLE; Schema: public; Owner: freecodecamp
--

CREATE TABLE public.exoplanet (
    exoplanet_id integer NOT NULL,
    name character varying(100) NOT NULL,
    star_id integer,
    discovery_method character varying(100),
    is_habitable boolean NOT NULL
);


ALTER TABLE public.exoplanet OWNER TO freecodecamp;

--
-- Name: exoplanet_exoplanet_id_seq; Type: SEQUENCE; Schema: public; Owner: freecodecamp
--

CREATE SEQUENCE public.exoplanet_exoplanet_id_seq
    AS integer
    START WITH 1
    INCREMENT BY 1
    NO MINVALUE
    NO MAXVALUE
    CACHE 1;


ALTER TABLE public.exoplanet_exoplanet_id_seq OWNER TO freecodecamp;

--
-- Name: exoplanet_exoplanet_id_seq; Type: SEQUENCE OWNED BY; Schema: public; Owner: freecodecamp
--

ALTER SEQUENCE public.exoplanet_exoplanet_id_seq OWNED BY public.exoplanet.exoplanet_id;


--
-- Name: galaxy; Type: TABLE; Schema: public; Owner: freecodecamp
--

CREATE TABLE public.galaxy (
    galaxy_id integer NOT NULL,
    name character varying(100) NOT NULL,
    size numeric,
    shape text,
    age integer NOT NULL,
    has_black_hole boolean NOT NULL
);


ALTER TABLE public.galaxy OWNER TO freecodecamp;

--
-- Name: galaxy_galaxy_id_seq; Type: SEQUENCE; Schema: public; Owner: freecodecamp
--

CREATE SEQUENCE public.galaxy_galaxy_id_seq
    AS integer
    START WITH 1
    INCREMENT BY 1
    NO MINVALUE
    NO MAXVALUE
    CACHE 1;


ALTER TABLE public.galaxy_galaxy_id_seq OWNER TO freecodecamp;

--
-- Name: galaxy_galaxy_id_seq; Type: SEQUENCE OWNED BY; Schema: public; Owner: freecodecamp
--

ALTER SEQUENCE public.galaxy_galaxy_id_seq OWNED BY public.galaxy.galaxy_id;


--
-- Name: moon; Type: TABLE; Schema: public; Owner: freecodecamp
--

CREATE TABLE public.moon (
    moon_id integer NOT NULL,
    name character varying(100) NOT NULL,
    planet_id integer,
    distance_from_planet numeric,
    has_water boolean NOT NULL,
    is_inhabited boolean NOT NULL
);


ALTER TABLE public.moon OWNER TO freecodecamp;

--
-- Name: moon_moon_id_seq; Type: SEQUENCE; Schema: public; Owner: freecodecamp
--

CREATE SEQUENCE public.moon_moon_id_seq
    AS integer
    START WITH 1
    INCREMENT BY 1
    NO MINVALUE
    NO MAXVALUE
    CACHE 1;


ALTER TABLE public.moon_moon_id_seq OWNER TO freecodecamp;

--
-- Name: moon_moon_id_seq; Type: SEQUENCE OWNED BY; Schema: public; Owner: freecodecamp
--

ALTER SEQUENCE public.moon_moon_id_seq OWNED BY public.moon.moon_id;


--
-- Name: planet; Type: TABLE; Schema: public; Owner: freecodecamp
--

CREATE TABLE public.planet (
    planet_id integer NOT NULL,
    name character varying(100) NOT NULL,
    star_id integer,
    diameter numeric,
    orbital_period integer,
    has_atmosphere boolean NOT NULL
);


ALTER TABLE public.planet OWNER TO freecodecamp;

--
-- Name: planet_planet_id_seq; Type: SEQUENCE; Schema: public; Owner: freecodecamp
--

CREATE SEQUENCE public.planet_planet_id_seq
    AS integer
    START WITH 1
    INCREMENT BY 1
    NO MINVALUE
    NO MAXVALUE
    CACHE 1;


ALTER TABLE public.planet_planet_id_seq OWNER TO freecodecamp;

--
-- Name: planet_planet_id_seq; Type: SEQUENCE OWNED BY; Schema: public; Owner: freecodecamp
--

ALTER SEQUENCE public.planet_planet_id_seq OWNED BY public.planet.planet_id;


--
-- Name: star; Type: TABLE; Schema: public; Owner: freecodecamp
--

CREATE TABLE public.star (
    star_id integer NOT NULL,
    name character varying(100) NOT NULL,
    galaxy_id integer,
    temperature integer,
    mass numeric NOT NULL,
    is_main_sequence boolean NOT NULL
);


ALTER TABLE public.star OWNER TO freecodecamp;

--
-- Name: star_star_id_seq; Type: SEQUENCE; Schema: public; Owner: freecodecamp
--

CREATE SEQUENCE public.star_star_id_seq
    AS integer
    START WITH 1
    INCREMENT BY 1
    NO MINVALUE
    NO MAXVALUE
    CACHE 1;


ALTER TABLE public.star_star_id_seq OWNER TO freecodecamp;

--
-- Name: star_star_id_seq; Type: SEQUENCE OWNED BY; Schema: public; Owner: freecodecamp
--

ALTER SEQUENCE public.star_star_id_seq OWNED BY public.star.star_id;


--
-- Name: exoplanet exoplanet_id; Type: DEFAULT; Schema: public; Owner: freecodecamp
--

ALTER TABLE ONLY public.exoplanet ALTER COLUMN exoplanet_id SET DEFAULT nextval('public.exoplanet_exoplanet_id_seq'::regclass);


--
-- Name: galaxy galaxy_id; Type: DEFAULT; Schema: public; Owner: freecodecamp
--

ALTER TABLE ONLY public.galaxy ALTER COLUMN galaxy_id SET DEFAULT nextval('public.galaxy_galaxy_id_seq'::regclass);


--
-- Name: moon moon_id; Type: DEFAULT; Schema: public; Owner: freecodecamp
--

ALTER TABLE ONLY public.moon ALTER COLUMN moon_id SET DEFAULT nextval('public.moon_moon_id_seq'::regclass);


--
-- Name: planet planet_id; Type: DEFAULT; Schema: public; Owner: freecodecamp
--

ALTER TABLE ONLY public.planet ALTER COLUMN planet_id SET DEFAULT nextval('public.planet_planet_id_seq'::regclass);


--
-- Name: star star_id; Type: DEFAULT; Schema: public; Owner: freecodecamp
--

ALTER TABLE ONLY public.star ALTER COLUMN star_id SET DEFAULT nextval('public.star_star_id_seq'::regclass);


--
-- Data for Name: exoplanet; Type: TABLE DATA; Schema: public; Owner: freecodecamp
--

INSERT INTO public.exoplanet VALUES (1, 'Proxima Centauri b', 5, 'Radial Velocity', true);
INSERT INTO public.exoplanet VALUES (2, 'TRAPPIST-1d', 5, 'Transit', true);
INSERT INTO public.exoplanet VALUES (3, 'Kepler-442b', 6, 'Transit', true);
INSERT INTO public.exoplanet VALUES (4, 'Kepler-62f', 6, 'Transit', true);
INSERT INTO public.exoplanet VALUES (5, 'HD 40307 g', 6, 'Radial Velocity', true);
INSERT INTO public.exoplanet VALUES (6, 'Gliese 581 d', 6, 'Radial Velocity', true);


--
-- Data for Name: galaxy; Type: TABLE DATA; Schema: public; Owner: freecodecamp
--

INSERT INTO public.galaxy VALUES (1, 'Milky Way', 1000000, 'Spiral', 13000, true);
INSERT INTO public.galaxy VALUES (2, 'Andromeda', 1500000, 'Spiral', 12000, true);
INSERT INTO public.galaxy VALUES (3, 'Whirlpool', 800000, 'Spiral', 10000, false);
INSERT INTO public.galaxy VALUES (4, 'Triangulum', 500000, 'Irregular', 9000, false);
INSERT INTO public.galaxy VALUES (5, 'Sombrero', 700000, 'Spiral', 11000, false);
INSERT INTO public.galaxy VALUES (6, 'Pinwheel', 600000, 'Spiral', 10000, false);


--
-- Data for Name: moon; Type: TABLE DATA; Schema: public; Owner: freecodecamp
--

INSERT INTO public.moon VALUES (1, 'Moon', 1, 384400, true, false);
INSERT INTO public.moon VALUES (2, 'Phobos', 2, 9376, false, false);
INSERT INTO public.moon VALUES (3, 'Deimos', 2, 23463, false, false);
INSERT INTO public.moon VALUES (4, 'Europa', 3, 671100, true, false);
INSERT INTO public.moon VALUES (5, 'Ganymede', 3, 1070400, true, false);
INSERT INTO public.moon VALUES (6, 'Callisto', 3, 1882700, true, false);
INSERT INTO public.moon VALUES (7, 'Titan', 6, 1221870, true, false);
INSERT INTO public.moon VALUES (8, 'Enceladus', 6, 237948, true, false);
INSERT INTO public.moon VALUES (9, 'Triton', 7, 354759, true, false);
INSERT INTO public.moon VALUES (10, 'Titania', 8, 436300, true, false);
INSERT INTO public.moon VALUES (11, 'Oberon', 8, 583500, true, false);
INSERT INTO public.moon VALUES (12, 'Charon', 9, 19591, true, false);
INSERT INTO public.moon VALUES (13, 'Eris', 10, 2326, false, false);
INSERT INTO public.moon VALUES (14, 'Gliese 581g Moon', 11, 230000, true, false);
INSERT INTO public.moon VALUES (15, 'Kepler-186f Moon', 12, 0, true, false);
INSERT INTO public.moon VALUES (16, 'Pluto Moon 7', 10, 2326, false, false);
INSERT INTO public.moon VALUES (17, 'Pluto Moon 8', 10, 2326, false, false);
INSERT INTO public.moon VALUES (18, 'Pluto Moon 9', 10, 2326, false, false);
INSERT INTO public.moon VALUES (19, 'Pluto Moon 10', 10, 2326, false, false);
INSERT INTO public.moon VALUES (20, 'Pluto Moon 11', 10, 2326, false, false);
INSERT INTO public.moon VALUES (21, 'Pluto Moon 12', 10, 2326, false, false);
INSERT INTO public.moon VALUES (22, 'Pluto Moon 13', 10, 2326, false, false);
INSERT INTO public.moon VALUES (23, 'Pluto Moon 14', 10, 2326, false, false);
INSERT INTO public.moon VALUES (24, 'Pluto Moon 15', 10, 2326, false, false);
INSERT INTO public.moon VALUES (25, 'Pluto Moon 16', 10, 2326, false, false);


--
-- Data for Name: planet; Type: TABLE DATA; Schema: public; Owner: freecodecamp
--

INSERT INTO public.planet VALUES (1, 'Earth', 1, 12742, 365, true);
INSERT INTO public.planet VALUES (2, 'Mars', 1, 6779, 687, false);
INSERT INTO public.planet VALUES (3, 'Venus', 1, 12104, 225, true);
INSERT INTO public.planet VALUES (4, 'Mercury', 1, 4879, 88, false);
INSERT INTO public.planet VALUES (5, 'Jupiter', 1, 139822, 4333, true);
INSERT INTO public.planet VALUES (6, 'Saturn', 1, 116464, 10759, true);
INSERT INTO public.planet VALUES (7, 'Neptune', 1, 49528, 60190, true);
INSERT INTO public.planet VALUES (8, 'Uranus', 1, 50724, 30685, true);
INSERT INTO public.planet VALUES (9, 'Pluto', 1, 2370, 90560, false);
INSERT INTO public.planet VALUES (10, 'Kepler-186f', 1, 12637, 130, true);
INSERT INTO public.planet VALUES (11, 'Gliese 581g', 1, 13253, 37, true);
INSERT INTO public.planet VALUES (12, 'HD 209458b', 1, 95429, 3, true);


--
-- Data for Name: star; Type: TABLE DATA; Schema: public; Owner: freecodecamp
--

INSERT INTO public.star VALUES (1, 'Sun', 1, 5778, 1989000000000000000000000000000, true);
INSERT INTO public.star VALUES (2, 'Sirius', 1, 9940, 2063000000000000000000000000000, true);
INSERT INTO public.star VALUES (3, 'Alpha Centauri A', 1, 5790, 2188000000000000000000000000000, true);
INSERT INTO public.star VALUES (4, 'Alpha Centauri B', 1, 5260, 1680000000000000000000000000000, true);
INSERT INTO public.star VALUES (5, 'Proxima Centauri', 1, 3042, 245000000000000000000000000000, false);
INSERT INTO public.star VALUES (6, 'Vega', 1, 9602, 2360000000000000000000000000000, true);


--
-- Name: exoplanet_exoplanet_id_seq; Type: SEQUENCE SET; Schema: public; Owner: freecodecamp
--

SELECT pg_catalog.setval('public.exoplanet_exoplanet_id_seq', 6, true);


--
-- Name: galaxy_galaxy_id_seq; Type: SEQUENCE SET; Schema: public; Owner: freecodecamp
--

SELECT pg_catalog.setval('public.galaxy_galaxy_id_seq', 6, true);


--
-- Name: moon_moon_id_seq; Type: SEQUENCE SET; Schema: public; Owner: freecodecamp
--

SELECT pg_catalog.setval('public.moon_moon_id_seq', 25, true);


--
-- Name: planet_planet_id_seq; Type: SEQUENCE SET; Schema: public; Owner: freecodecamp
--

SELECT pg_catalog.setval('public.planet_planet_id_seq', 12, true);


--
-- Name: star_star_id_seq; Type: SEQUENCE SET; Schema: public; Owner: freecodecamp
--

SELECT pg_catalog.setval('public.star_star_id_seq', 6, true);


--
-- Name: exoplanet exoplanet_name_key; Type: CONSTRAINT; Schema: public; Owner: freecodecamp
--

ALTER TABLE ONLY public.exoplanet
    ADD CONSTRAINT exoplanet_name_key UNIQUE (name);


--
-- Name: exoplanet exoplanet_pkey; Type: CONSTRAINT; Schema: public; Owner: freecodecamp
--

ALTER TABLE ONLY public.exoplanet
    ADD CONSTRAINT exoplanet_pkey PRIMARY KEY (exoplanet_id);


--
-- Name: galaxy galaxy_name_key; Type: CONSTRAINT; Schema: public; Owner: freecodecamp
--

ALTER TABLE ONLY public.galaxy
    ADD CONSTRAINT galaxy_name_key UNIQUE (name);


--
-- Name: galaxy galaxy_pkey; Type: CONSTRAINT; Schema: public; Owner: freecodecamp
--

ALTER TABLE ONLY public.galaxy
    ADD CONSTRAINT galaxy_pkey PRIMARY KEY (galaxy_id);


--
-- Name: moon moon_name_key; Type: CONSTRAINT; Schema: public; Owner: freecodecamp
--

ALTER TABLE ONLY public.moon
    ADD CONSTRAINT moon_name_key UNIQUE (name);


--
-- Name: moon moon_pkey; Type: CONSTRAINT; Schema: public; Owner: freecodecamp
--

ALTER TABLE ONLY public.moon
    ADD CONSTRAINT moon_pkey PRIMARY KEY (moon_id);


--
-- Name: planet planet_name_key; Type: CONSTRAINT; Schema: public; Owner: freecodecamp
--

ALTER TABLE ONLY public.planet
    ADD CONSTRAINT planet_name_key UNIQUE (name);


--
-- Name: planet planet_pkey; Type: CONSTRAINT; Schema: public; Owner: freecodecamp
--

ALTER TABLE ONLY public.planet
    ADD CONSTRAINT planet_pkey PRIMARY KEY (planet_id);


--
-- Name: star star_name_key; Type: CONSTRAINT; Schema: public; Owner: freecodecamp
--

ALTER TABLE ONLY public.star
    ADD CONSTRAINT star_name_key UNIQUE (name);


--
-- Name: star star_pkey; Type: CONSTRAINT; Schema: public; Owner: freecodecamp
--

ALTER TABLE ONLY public.star
    ADD CONSTRAINT star_pkey PRIMARY KEY (star_id);


--
-- Name: exoplanet exoplanet_star_id_fkey; Type: FK CONSTRAINT; Schema: public; Owner: freecodecamp
--

ALTER TABLE ONLY public.exoplanet
    ADD CONSTRAINT exoplanet_star_id_fkey FOREIGN KEY (star_id) REFERENCES public.star(star_id);


--
-- Name: moon moon_planet_id_fkey; Type: FK CONSTRAINT; Schema: public; Owner: freecodecamp
--

ALTER TABLE ONLY public.moon
    ADD CONSTRAINT moon_planet_id_fkey FOREIGN KEY (planet_id) REFERENCES public.planet(planet_id);


--
-- Name: planet planet_star_id_fkey; Type: FK CONSTRAINT; Schema: public; Owner: freecodecamp
--

ALTER TABLE ONLY public.planet
    ADD CONSTRAINT planet_star_id_fkey FOREIGN KEY (star_id) REFERENCES public.star(star_id);


--
-- Name: star star_galaxy_id_fkey; Type: FK CONSTRAINT; Schema: public; Owner: freecodecamp
--

ALTER TABLE ONLY public.star
    ADD CONSTRAINT star_galaxy_id_fkey FOREIGN KEY (galaxy_id) REFERENCES public.galaxy(galaxy_id);


--
-- PostgreSQL database dump complete
--

