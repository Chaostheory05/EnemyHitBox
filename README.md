# EnemyHitBox
// This code is from Epitome's Tutorial https://www.youtube.com/watch?v=b8YUfee_pzc&t=23003s

using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class EnemyHitbox : Collidable 
{
	public int damage;
	public float pushForce;

	protected override void OnCollide(Collider2D coll)
	{
		if (coll.tag == "Fighter" && coll.name == "Player") 
		{
			
			Damage dmg = new Damage {
				damageAmount = damage,
				origin = transform.position,
				pushForce = pushForce
			};

			coll.SendMessage ("ReceiveDamage", dmg);

		}
	}

}
