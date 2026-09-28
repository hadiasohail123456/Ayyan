## step 1
create nextjs project
open cmd 
cd desktop
create-next-app@latest my name--
ayyan_next.js
npm install@supabase/supabse.js
npm run dev
localhost:3000
# step 2
create supabase project account on supabase.com

# step 3
create nextjs project

irst, I created a project in Supabase and created the database for my Note App.

Supabase provides the database where my notes will be stored.

Create the .env.local File

Next, I created a .env.local file in the main folder of my Next.js project.

The .env.local file stores the Supabase project URL and publishable key.

NEXT_PUBLIC_SUPABASE_URL=https://anyprojectid.supabase.co
NEXT_PUBLIC_SUPABASE_PUBLISHABLE_KEY=sb_publishable_key

The actual URL and key are copied from:

Supabase Dashboard → Project Settings → API

Install Supabase

I installed the Supabase JavaScript library using the following command:

npm install @supabase/supabase-js

This package allows my Next.js application to communicate with Supabase.

Create the Supabase Connection

Inside the lib folder, I created a file named:

lib/supabase.js

I added the following code:

import { createClient } from '@supabase/supabase-js';

export const supabase = createClient(
  process.env.NEXT_PUBLIC_SUPABASE_URL,
  process.env.NEXT_PUBLIC_SUPABASE_PUBLISHABLE_KEY
);

The createClient() function creates a connection between my Next.js application and my Supabase project.

The environment variables provide the Supabase URL and publishable key.


 Import Supabase into Next.js

After creating the connection, I imported the Supabase client into my Next.js page:

import { supabase } from '@/lib/supabase';


Insert Data into Supabase

To save information, I used the insert() method.

For example:

const { error } = await supabase
  .from('notes')
  .insert({
    title,
    content
  });

Here:

.from('notes') means that I am working with the notes table.
.insert() adds new information to the table.
title and content are the values that I want to sav

Select Data from Supabase

To get information from the database, I used the select() method:

const { data: notes, error } = await supabase
  .from('notes')
  .select('*');

Here:

.from('notes') selects the notes table.
.select('*') gets all columns.
data contains the notes received from Supabase.
error contains an error if the database request fails.Create a Form

I created a form in Next.js to allow the user to enter note information.

For example:

<form action={addNote}>
  <label>Title</label>
  <input type="text" name="title" required />

  <label>Content</label>
  <textarea name="content" required />

  <button type="submit">Add Note</button>
</form>

When the user submits the form, the information is sent to the addNote function.


